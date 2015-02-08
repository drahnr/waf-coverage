## waf-coverage

[![Join the chat at https://gitter.im/drahnr/waf-coverage](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/drahnr/waf-coverage?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

If you pass `--with-coverage` flag to waf, coverage files will be generated.


### Usage

Just copy the `coverage.py` file to your project directory (where the desired waf file is, other wise you have to adjust the `tooldir=` path)

```python
def options(opt):
    opt.load('coverage', tooldir='.')
    ...

def configure(cfg):
    cfg.load('coverage', tooldir='.')
    ...


def build(bld):
    # build your regular binary here
    mybin = bld.program(
		features = ['c', 'coverage'],
		...
		)

    # build any number of tests, here we use my other pet project `unites`
	atest = bld.program(
		features = ['c', 'coverage', 'unites'],
		target = 'multi-client-test',
		source = ['test/multi-client.c'],
		includes = ['src'],
		...
		)

```
