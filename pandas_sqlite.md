# 
```python
import pandas as pd
import numpy as np
from sqlalchemy import create_engine

frame = pd.DataFrame(np.arange(20).reshape(4,5),
                     columns=['white', 'red', 'blue', 'black', 'green'])


engine= create_engine('sqlite:///a888168.db')
print(frame)
frame.to_sql('colors', engine)
```
