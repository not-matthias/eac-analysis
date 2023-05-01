# Driver Analysis

## Current goals

- [ ] Symbolically trace the handlers
- [ ] Lift to LLVM IR and optimize
- [ ] Profit


## Handler Offset Table

Offsets to the specific handlers are stored in a table. They are loaded in reverse onto the stack.

![image](https://user-images.githubusercontent.com/26800596/235468702-9ceaa5db-5d9f-4c2c-a378-c49aae904b91.png)

## Next handler calculation

First the offsets are loaded onto the stack, then we use the first offset to jump to the handler:

![image](https://user-images.githubusercontent.com/26800596/235469526-9853c438-883b-46c3-94cd-acc35a95925d.png)

Handler address: `0x14cc43990 -0x0c1ce70e` (last entry of the table cause it's stored in reverse on the stack)

Patch it in BinaryNinja and repeat.

![image](https://user-images.githubusercontent.com/26800596/235470497-5bbcbffb-55d7-4179-b670-6ece0ff875da.png)
