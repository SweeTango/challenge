# challenge

Insert '*' or '/' between the decimals to make the following number sentence true

~~~
0.1 __ 0.5 __ 0.6 __ 0.12 __ 0.2 __ 0.25 __ 0.5__ 0.1 = 1
~~~

Code:

~~~
#!/usr/bin/python3

data = [0.1, 0.5, 0.6, 0.12, 0.2, 0.25, 0.5, 0.1]

ops = len(data) - 1     # Number of operators
loops = 1 << ops        # Total combinations

for i in range(loops):
    s = str(data[0])
    for j in range(ops):
        if i & (1 << j):
            s += '*'
        else:
            s += '/'
        s += str(data[j+1])
    result = round(eval(s), 2)
    if (result == 1):
        print(s, '=', result, ' <- YAHOO!!')
~~~

Output:

~~~
$ python3 challenge.py 
0.1/0.5/0.6*0.12/0.2*0.25/0.5/0.1 = 1.0  <- YAHOO!
0.1/0.5*0.6/0.12*0.2*0.25/0.5/0.1 = 1.0  <- YAHOO!
0.1*0.5/0.6*0.12/0.2/0.25*0.5/0.1 = 1.0  <- YAHOO!
0.1*0.5*0.6/0.12*0.2/0.25*0.5/0.1 = 1.0  <- YAHOO!
0.1*0.5*0.6/0.12/0.2/0.25/0.5*0.1 = 1.0  <- YAHOO!
0.1/0.5*0.6/0.12/0.2/0.25*0.5*0.1 = 1.0  <- YAHOO!
~~~
