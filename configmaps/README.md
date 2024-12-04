Used to store non confidential data in the form of key value pairs.

Pods consume ConfigMaps as env variable, cmd line agrs, config file from a volume.

key values can be given as property-like keys or file-like keys
first_name: "John"
game.properties: | enemy.types=aliens