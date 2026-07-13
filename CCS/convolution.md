## Code
``` c
#include <stdio.h>

int m=6;
int n=6;
int i=0,j;
int x[15]={1,2,3,4,5,6,0,0,0,0,0,0};
int h[15]={1,2,3,4,5,6,0,0,0,0,0,0};
int y[20];

main()
{

	for(i=0;i<m+n-1;i++)
	{
		y[i]=0;
		for(j=0;j<=i;j++)
            y[i]+=x[j]*h[i-j];
	}
	for(i=0;i<m+n-1;i++)
		printf("%d \n",y[i]);

	while(1);
}
```

## Output
``` c
	[C674X_0] 1
	4
	10
	20
	35
	56
	70
	76
	73
	60
	36
```
