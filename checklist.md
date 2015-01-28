# NC can not start
```
/var/folders/_2/zgvz3_dd3gb_7pwy32dwgrzw0000gn/T/nc1/iodevice0/asterix_root_metadata/nc1_iodevice0/.asterix_root_metadata (No such file or directory)
```

Normally it means the server start from the old configuration, but the metadata file is missing. 
To start from scratch, clean all the txn folder to skip the recovery process. The default recovery
folder is under "target/txnLogDir"
