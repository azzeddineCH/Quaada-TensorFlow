# TF Tensors and operations

Created: Feb 18, 2021 10:18 PM
Last Edited Time: Mar 27, 2021 9:34 PM
Status: done
Week: Week 2
presented: No

- Tensors in Tensorflow are just like ndarray in numpy 😁  ! for example:

```python
x = tf.constant(value=....,dtype=tf.int8) # x = np.array(value=..., dtype=np.int8)
x = tf.reshape(x,shape=(..)). # x = tf.reshape(x,shape=(...))
```

- Tensoflow support importing from and exporting to Numpy, and even more !

```python
np_x = x.numpy()
tf_x = tf.constant(np_x)

# you don't have to explictly import your numpy/list
tf.reshape(np_x, shape=(...)) # this work too !
```

---

- `tf.constant` are immutable (can't chage their state), use `tf.Varaible` instead 😉  !

```python
my_tensor = tf.constant([[1.0, 2.0], [3.0, 4.0]])
my_variable = tf.Variable(my_tensor)

print(my_variable)
```

- `tf.Variable` represents a tensor whose value can be changed by running ops on it (used the TF keras API) like:

```python
a = tf.Variable([2.0, 3.0])
a.assign_add([1,1])

prin(a)
```

- you can't mutate the variable size or data type

```python
a = tf.Variable([2.0, 3.0])
# This will keep the same dtype, float32
a.assign([1, 2]) 
# Not allowed as it resizes the variable: 
try:
  a.assign([1.0, 2.0, 3.0])
except Exception as e:
  print(f"{type(e).__name__}: {e}")
```

- All tensors' operations are applicable on `tf.Varaible`

- Varaibles can be assigned names

```python
my_tensor = tf.constant([1],dtype=tf.float32)
a = tf.Variable(my_tensor, name="GDG")

print(a)
```