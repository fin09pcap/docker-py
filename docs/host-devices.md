# Access to devices on the host

If you need to directly expose some host devices to a container, you can use
the devices parameter in the `host_config` param in `Client.create_container`
as shown below:

```python
c.create_container(
    'busybox', 'true', host_config=docker.utils.create_host_config(devices=[
        '/dev/sda:/dev/xvda:rwm'
    ])
)
```

Each string is a single mapping using the colon (':') as the separator. So the
above example essentially allow the container to have read write permissions to
access the host's /dev/sda via a node named /dev/xvda in the container. The
devices parameter is a list to allow multiple devices to be mapped.
