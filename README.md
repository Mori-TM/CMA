# CMA
The memory allocater/manager for my game engine and openvk

```C
#include "CMA.h"

typedef struct
{
    int var;
} Dummy;

int main()
{
    //first create a memory zone
    CMA_MemoryZone Mem = CMA_Create(sizeof(Dummy));

    Dummy in;
    in.var = 22;
    //in the zone you can push your data
    CMA_Push(&Mem, &in);

    //and get the data from the zone
    Dummy* out = (Dummy*)CMA_GetAt(&Mem, 0);
    //checking if out != null is very important!!
    if (out != NULL)
        printf("%d", out->var);

    //and you can free the memory at an index
    CMA_Pop(&Mem, 0);

    //this fill free all memory in the zone
    CMA_Destroy(&Mem);
}
```
