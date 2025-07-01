`volatile` tells the compiler not to optimise anything that has to do with the `volatile` variable.

It will tell the compiler not to cache the value of the variable and to take the value of the given `volatile` variable from main memory every time it encounters it.

Usually used in situations involving where the value of a variable can change without action from the visible code. 
1) When you interface with hardware that changes the value itself
2) When there is another thread running that also uses the variable
3) When there is a signal handler that might change the value of the variable
4) When the value can be modified by the OS or any interrupt.

#### Example

```c
typedef struct
{
  int command;
  int data;
  int isBusy;
} MyHardwareGadget;
```

```c
void SendCommand(MyHardwareGadget* gadget, int command, int data)
{
  // wait while the gadget is busy:
  while (gadget->isBusy)
  {
    // do nothing here.
  }
  // set data first:
  gadget->data    = data;
  // writing the command starts the action:
  gadget->command = command;
}
```

This can fail because the compiler is free to change the order in which data and commands are written.
- Would cause our `gadget` to issue commands with the previous data-value.
- While loop will be optimised out. The compiler will try to be clever, read the value of isBusy just once and then go into a infinite loop. 

#### Corrected version
```c
void SendCommand(volatile MyHardwareGadget* gadget, int command, int data)
{
  // wait while the gadget is busy:
  while (gadget->isBusy)
  {
    // do nothing here.
  }
  // set data first:
  gadget->data    = data;
  // writing the command starts the action:
  gadget->command = command;
}
```

This forces the compiler to do what you wrote, it cannot remove the memory assignments, it can't cache variables in registers and it
1) It cannot remove memory assignments
2) It cannot cache variables in registers
3) It cannot change the order of assignments

### Example 2

```c
int quit = 0;
while (!quit)
{
    /* very small loop which is completely visible to the compiler */
}
```

The compiler notices the loop body does not touch the quit variable and converts the loop to a `whil(true)` loop.

Even if the `quit` variable is set on the signal handler for `SIGINT` and `SIGTERM` the compiler has no way to know that, but if the `quit` variable is declared `volatile` the compiler is forced to load it every time, because it can be modified elsewhere.
