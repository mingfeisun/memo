## Useful python libraries
* Mingfei Sun
* Created: 2018-01-24
* Updated: 2018-01-24


### [tqdm](https://pypi.org/project/tqdm/)

<img src="https://warehouse-camo.cmh1.psfhosted.org/1e5bc2088d8bd1edf2ddaaffa21435c0fee10a03/68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f7471646d2f7471646d2f6d61737465722f696d616765732f7471646d2e676966" alt="tqdm" width="550px"/>

### [retry](https://pypi.org/project/retry/)

``` python
from retry import retry

@retry()
def make_trouble():
    '''Retry until succeed'''

@retry(ZeroDivisionError, tries=3, delay=2)
def make_trouble():
    '''Retry on ZeroDivisionError, raise error after 3 attempts, sleep 2 seconds between attempts.'''
```
