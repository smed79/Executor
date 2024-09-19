# Executor
Real-time text formatting tool. Use {command *arguments}>. Example: {ip}> (without args), {randomize 2 9}> (2 args). Type {help}> to see all commands.


# Writing custom scripts
Write function what you need. Do not forget about errors handling. Function must always return string.

```python
def ip():
    try:
        url = "https://api.myip.com"
        with urllib.request.urlopen(url) as response:
            data = response.read().decode()
            json_data = json.loads(data)
            ip = json_data.get("ip", "Not found")
            country = json_data.get("country", "Not found")
            return f"IP: {ip}, {country}"
    except Exception as e:
        return str(e)
```

At the end of the file, include the commands in the script and add the author's name (optional):

```python
COMMANDS = {
    "ip": ip,
}

AUTHOR = "name"
```
