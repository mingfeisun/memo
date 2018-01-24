## Python create figures for paper
* Mingfei Sun
* Created: 2018-01-24
* Updated: 2018-01-24

If encouter errors like font not found, then
```bash
# install fonts
sudo apt-get install msttcorefonts -qq
# remove cached data
rm -rf ~/.cached/matplotlib/
```

```python
import pandas
import numpy
import matplotlib.pyplot as plt

plt.rcParams["font.family"] = "Times New Roman"
plt.rcParams["font.size"] = '22'
# plt.rcParams["font.weight"] = 'bold'
# plt.rcParams['axes.labelweight'] = 'bold'
plt.rcParams['axes.labelsize'] = '22'

from scipy.signal import wiener

def smooth(x,window_len=11,window='hamming'):
    if x.ndim != 1:
        raise ValueError, "smooth only accepts 1 dimension arrays."
    if x.size < window_len:
        raise ValueError, "Input vector needs to be bigger than window size."
    if window_len<3:
        return x
    if not window in ['flat', 'hanning', 'hamming', 'bartlett', 'blackman']:
        raise ValueError, "Window is on of 'flat', 'hanning', 'hamming', 'bartlett', 'blackman'"

    s=numpy.r_[x[window_len-1:0:-1],x,x[-1:-window_len:-1]]
    if window == 'flat': #moving average
        w=numpy.ones(window_len,'d')
    else:
        w=eval('numpy.'+window+'(window_len)')

    y=numpy.convolve(w/w.sum(),s,mode='valid')
    return y

data = numpy.load("neoface_raw.npy")
label = numpy.load("neoface_raw_label.npy")

fig = plt.figure(0, figsize=(15, 4.5))

font_name = {'fontname':'Times'}

plot1 = plt.subplot(121)

x = numpy.arange(300)/30.0
y = numpy.copy(data[20, :, 0])

plt.plot(x, y, label='Original', color='grey')
plt.plot(x, smooth(y)[5:305], label='Filtered', color='red')

plt.ylim(0, 1)
plt.xlabel('Time t (s)', fontstyle='italic')
plt.ylabel('Closeness degree', fontstyle='italic')
plt.setp(plot1.get_xticklabels())
plt.setp(plot1.get_yticklabels())

plot2 = plt.subplot(122, sharex=plot1, sharey=plot1)

y = numpy.copy(data[20, :, 1])

plt.plot(x, y, label='Original', color='grey')
plt.plot(x, smooth(y)[5:305], label='Filtered', color='red')

plt.xlabel('Time t (s)', fontstyle='italic')
plt.ylim(0, 1)
# plt.setp(plot2.get_yticklabels(), visible=False)

plt.setp(plot2.get_xticklabels())
plt.setp(plot2.get_yticklabels(), visible=False)

# plt.legend(loc='center left', bbox_to_anchor=(1, 0.5))
# plt.legend(loc='best')

fig.tight_layout()
fig.savefig('test.png')

# plt.show()
```
