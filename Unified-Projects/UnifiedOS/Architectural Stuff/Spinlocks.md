This are a way of blocking code from being run multiple times at once. This is mainly important when writing to disks and allocating memory as we don't want to access the same position at once.

They make use of the compilers atomic features.
```CPP TI="EG"
acquireLock(lock){
	while (__atomic_exchange_n(lock, 1, __ATOMIC_ACQUIRE)){
		asm("pause");
	}
}
```