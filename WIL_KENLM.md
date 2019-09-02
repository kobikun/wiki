# kenlm

* https://github.com/kpu/kenlm
* Faster and Smaller Language Model Queries
* detail about Kenlm : https://kheafield.com/code/kenlm/

# max-order setting

* kenlm's default max-order is 6 (6 gram)

## C++

```bash
mkdir build
cd build
cmake3 ../ -DKENLM_MAX_ORDER=10
make -j 10
```

## python

```
python ./setup.py build --max_order=10
python ./setup.py install
```
