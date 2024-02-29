![](Pasted%20image%2020240229135714.png)
```python
from fnmatch import *

for i in range(42, 2*10**8, 42):
	if fnmatch(str(i), '?2*4*0') and not(fnmatch(str(i), '1*7*')) and i % 42 == 0:
		print(i, i / 42)
```