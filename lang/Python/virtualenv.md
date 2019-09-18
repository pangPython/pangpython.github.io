
> 创建一个独立的Python运行环境，命名为venv
> virtualenv --no-site-packages venv
> 已经安装到系统Python环境中的所有第三方包都不会复制过来，这样，我们就得到了一个不带任何第三方包的“干净”的Python运行环境。

> source venv/bin/activate