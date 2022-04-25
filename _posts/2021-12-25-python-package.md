# How to install python in multiple ways ?

Your GF meets problems always because of coding on Windows？？？？
![TAS~HWF10 6%5BWM5X7~6TG](https://user-images.githubusercontent.com/60593268/147386243-2ca73d87-de45-429b-8dec-e5b7e8d8171e.jpg)

pip wanna complie source code to `*whl` and install it which depends on Visual C++. There are some methods to install source code without VS:

- Pypi: The package is published with source code or `*.whl` sometimes.

![image](https://user-images.githubusercontent.com/60593268/147386344-8d469344-bf46-4d5e-bd7d-940c0c0f9bad.png)

```bash
pip install package.whl
```

- [lfd.uci.edu](https://www.lfd.uci.edu/~gohlke/pythonlibs/): The UC Irvine Fluorescence Dynamics Laboratory provides you with an unofficial python package of binary wheel files under Windows 64 bits
just `Ctr + F` to search your package and install it by using the command above.

- [pipwin](https://pypi.org/project/pipwin/): pipwin is a complementary tool for pip on Windows. pipwin installs unofficial python package binaries for windows provided by Christoph Gohlke here http://www.lfd.uci.edu/~gohlke/pythonlibs/

QuickStart
```bash
>> pip install pipwin
>> pipwin search cv

Did you mean any of these ?

  * cvxopt
  * opencv-python
  * abcview
  * cvxpy

>> pipwin install opencv-python

>> pipwin install numpy>=1.11
```
