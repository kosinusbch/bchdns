# BCH-DNS for bch.sx

This is a front-end implementation of BCH-DNS that allows you to create and manage .bch.sx domain names. If you register "bitcoinwallet", it will be accessible through bitcoinwallet.bch.sx and in the future just bitcoinwallet.bch

## How does this work?

Each action is done on the blockchain through a OP_RETURN transaction. All changes are public, verifiable and auditable. The first person to register a domain keeps it forever,

## Actions

A list of actions currently supported by this implementation of BCH DNS. Content in quotes are a new push data. First push data is the protocol identifier registered for BCH DNS, second pushdata is version number 0(x) then up to 1296 different actions starting at 00-99 ending at 0A-ZZ, third is the domain you want to register or modify, fourth which is optional is the data to set. If left blank it will be deleted/unset. The first person to register the domain gets to keep it. Only confirmed (1-conf+) actions are considered valid.

Register domain

`"0x04008080" "0x00" "bcash"`

Delete/Free domain

`"0x04008080" "0x01" "bcash"`

Set/update A record

`"0x04008080" "0x02" "bcash" "127.0.0.1"`

Set/update CNAME record

`"0x04008080" "0x03" "bcash" "example.com"`

## How do we avoid collisions and resolve conflicting domain registrations?

TBA