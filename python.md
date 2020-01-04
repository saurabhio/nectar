### Python

```
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt install python3.8

# list all versions installed
ls -l /usr/bin/python*
```

```
regular_variables
CONS_TANTS
function_names
ClassNames
FactoryFunctionNames
_non_public_properties
conflicting_names_


"is" expressions evaluate to True if two variables point to the same object, i.e having same id
"==" evaluates to True if the objects referred to by the variables are equal in value


When a module is imported, then it gets executed immediately.

When a function is defined, all its input arguments are exceuted.
And when a function is called (any number of times), input arguments are not excuted.
So, declare mutable default input arguments as None


Functions are first-class citizens in Python. They can be passed as arguments to other functions, 
returned as values from other functions, and assigned to variables and stored in data structures.

def myfunc(a, b):
    return a + b

funcs = [myfunc]
funcs[0](2, 3)
```


```
print(mem_profile.memory_usage_resource())


print(f"{right:>10} | {left:<10} | {center:^10} | {12.34567":{width}.{precision}}")


large_number = 10_000_000
print(f'{large_number:,}')


x = 10 if condition else 0


for name, phone in zip(name_list, phone_list):
  ...


*_, z = (1, 2, 3, 4, 5)
a, b, *c, d = (1, 2, 3, 4, 5)


anydict.get('name', 'there')


for x in haystack:
    if x == 'needle':
        print('Found')
        break
 else:
     # when no break happens
     print('Not Found')


d = { f(k) : g(v) for k, v in zip(a,b) }


# to hide password typing in console
p = getpass.getpass("Password: ")  # rather than   input("Password: ")


def switch_func(operator, x, y):
    return {
        'add': lambda: x + y,
        'sub': lambda: x - y,
        'mul': lambda: x * y,
        'div': lambda: x / y,
    }.get(operator, lambda: None)()

switch_func('mul', 2, 8)


if 1 in (x,y,z):
    print("ok")
// or
if x or y or z:
     print("ok")
// or
if any((x,y,z)):
    print("ok")
    

timeit.timeit('[x+x for x in x_list]', number=10000)


def myfunc(x, y, z):
    print(x, y, z)

tuple_vec = (1, 0, 1)
dict_vec = {'x': 1, 'y': 0, 'z': 1}

myfunc(*tuple_vec) # 1, 0, 1
myfunc(**dict_vec) # 1, 0, 1


l = []
for p in ppl:
    if p < thresh:
        continue
     l.append(afunc(p))

# better
l = [afunc(p) for p in ppl if p >= thresh]

# or
l = list(map(afunc, filter(condition_func, ppl)))



l = []
for x in xcoord:
    for y in ycoord:
        l.append((x,y))
        
# better
l = [(x,y) for x in xcoord for y in ycoord]

# or
l = list(itertools.product(xcoord, ycoord))


d = {}
for key, value in tall_buildings.items():
    if 'tower' not in key:
        continue
     d[key] = afunc(value)
     
# better
d = {k:afunc(v) for k,v in tall_buildings.items() if 'tower' in k}


```



