# FortiTopology

Convert Fortigate .config file to a Topology using Python

```
import re

def extract_info(file):
    # Regular expression pattern to match network objects
    pattern = re.compile(r'config firewall address\n\s+edit (.+)\n\s+set subnet (.+) (.+)')
    
    network_objects = {}
    
    with open(file, 'r') as f:
        for line in f:
            match = pattern.search(line)
            if match:
                name, subnet, subnet_mask = match.groups()
                network_objects[name] = (subnet, subnet_mask)
    
    return network_objects

def create_topology(network_objects):
    # Code to create the topology using a tool such as Matplotlib or NetworkX
    # ...

if __name__ == '__main__':
    file = 'fortigate.config'
    network_objects = extract_info(file)
    create_topology(network_objects)
```

This code uses regular expressions to extract the network objects from the Fortigate configuration file. The network objects are stored in a dictionary, where the key is the name of the object and the value is a tuple of the subnet and subnet mask. The create_topology function can then be used to create the network topology using a tool such as Matplotlib or NetworkX.

Note: This is just a sample code and may need to be adapted to your specific use case. The exact solution will depend on the format of the Fortigate configuration file and your specific requirements for the network topology.
