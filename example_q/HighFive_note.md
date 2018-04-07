# To use HDF5 save std::vector and so on

## First one need to install HDF5 library on computer


<https://blog.csdn.net/luoying_1993/article/details/53228473>

<https://support.hdfgroup.org/ftp/HDF5/current/src/hdf5-1.10.1.tar>

```bash
dpkg -L libhdf5-dev
```



## Examples copied from the github and /src/example

### Compile

The way to compile is,

```console
c++ -o program -I/path/to/highfive/include source.cpp  -lhdf5
```

In this case the path to highfive is:

```console
g++ -o create_dataset_double -I/home/haixin/Documents/HighFive/include -I/usr/local/hdf5/include/ create_dataset_double.cpp -lhdf5
```

H5Ipublic.h located

```console
/usr/include/hdf5/serial/H5Ipublic.h
/usr/local/hdf5/include/H5Ipublic.h
/usr/share/HDF5/1.10.2/include/H5Ipublic.h
```

Reported error

```console
haixin@haixin-desktop:~/Documents/HighFive/example_q$ g++ -o create_dataset_double -I/home/haixin/Documents/HighFive/include -I/usr/local/hdf5/include/ create_dataset_double.cpp -lhdf5
/usr/bin/ld: cannot find -lhdf5
collect2: error: ld returned 1 exit status
```

Solution: 

<https://askubuntu.com/questions/702145/c-header-files-for-hdf5-are-missing?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa>


```console
h5c++ -o create_dataset_double -I/home/haixin/Documents/HighFive/include -I/usr/local/hdf5/include/ create_dataset_double.cpp -lhdf5
```

If I use,

```
h5c++ -o create_dataset_double -I/home/haixin/Documents/HighFive/include create_dataset_double.cpp -lhdf5
```

also works _It seems that g++ cannot find hdf5 properly_, but it's not true.

But if I try

```console
g++ -o create_dataset_double -I/home/haixin/Documents/HighFive/include -L/usr/local/hdf5/lib -I/usr/local/hdf5/include create_dataset_double.cpp -lhdf5
```

_works!_