# Tensoflow Dataset API

Created: Feb 18, 2021 10:18 PM
Last Edited Time: Mar 27, 2021 9:33 PM
Status: done
Week: Week 2
presented: No

Reference: Tensoflow documentation website

- 0. [tf.data](http://tf.data) API explained

- 1. Extracting data from different sources

    - From data in memory

        if all the data fits in memory, the easiest way to load them is to convert them into `tf.Tensor` or as `np.ndarray` (remember np.ndarray and tensorflow are friends 😉  ) and pass them into `from_tensor_slices`

        ```python
        train, _ = tf.keras.datasets.fashion_mnist.load_data()
        images, labels = train
        dataset = tf.data.Dataset.from_tensor_slices((images, labels))
        print(dataset)
        ```

        Don't use list to express the nested structer of your dataset, instead use: tuple, dict, NamedTuple

        ```python
        train, _ = tf.keras.datasets.fashion_mnist.load_data()
        images, labels = train

        train = [images,labels]
        dataset = tf.data.Dataset.from_tensor_slices(train) # this won't express you input/output structer

        train = dict(images=images, labels=labels)
        dataset = tf.data.Dataset.from_tensor_slices((train)) # this is OK !!
        print(dataset)
        ```

    - From python generators

        - What's a generator in Python 👇🏼 ?

            generator-function is defined like a normal function, but whenever it needs to generate a value, it does so with the yield keyword rather than return.

            If the body of a def contains yield, the function automatically becomes a generator function.

            ```python
            # A generator function that yields 1 for first time, 
            # 2 second time and 3 third time 
            def simpleGeneratorFun(): 
                yield 1            
                yield 2            
                yield 3            
               
            # Driver code to check above generator function 
            gen = simpleGeneratorFun()
            for value in gen:  
                print(value)
            ```

        - consume a generator in tensorflow

            After you setup your generator, pass it to `tf.data.Dataset.from_generator` :

            - `args` a list of arguments to pass to your generator
            - `output_types` a nested structer of your output types
            - `output_shapes` a nested structer of your output shapes

            ```python
            ds_counter = tf.data.Dataset.from_generator(count, args=[files_list], output_types=(tf.float64,tf.uint8), output_shapes = ((64,64,4),())
            ```

    - From text files

        if you a dataset ditributed across a set of text files, then `tf.data.TextLineDataset` is the one for you, create an instance by passing:

        - `filenames` : list of tfrecord filenames or single element
        - `compression_type (Optional)` : compression type `ZLIB`, `GLIB`, `None`
        - `buffer_size (Optional)`: the number of bytes in the read buffer
        - `num_parallel_reads (Optiaonl)` : the number of files to read in parallel

        ```python
        titanic_file = tf.keras.utils.get_file("train.csv", "https://storage.googleapis.com/tf-datasets/titanic/train.csv")
        titanic_lines = tf.data.TextLineDataset(titanic_file)

        for line in titanic_lines.take(10):
          print(line.numpy())
        ```

        **TIPS**: you can use a generator, pass the file as argument and yield line by line

    - From CSV data

        CSV data takes the form of tabular shape as shown below 👇🏼

        ![Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-21_at_19.08.00.png](Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-21_at_19.08.00.png)

        **TIPS:** if your data fits well in memory load it with panads as a data frame and pass it to `from_tensor_slices` as a dict as shown below 👇🏼

        ```python
        df = pd.read_csv(csv_file)
        my_dataset = tf.data.Dataset.from_tensor_slices(dict(df))
        ```

        ---

        - You can also create a TF dataset from a CSV using a high level API utility function `tf.data.experimental.make_csv_dataset`

            ```python
            titanic_file = tf.keras.utils.get_file("train.csv", "https://storage.googleapis.com/tf-datasets/titanic/train.csv")
            titanic_dataset = tf.data.experimental.make_csv_dataset(titanic_file, batch_size=4,label_name="survived")
            ```

        - You can create a dataset from CSV file using a low level API class `CsvDataset`

            ```python
            titanic_types  = [tf.int32, tf.string, tf.float32, tf.int32, tf.int32, tf.float32, tf.string, tf.string, tf.string, tf.string] 
            dataset = tf.data.experimental.CsvDataset(titanic_file, titanic_types , header=True)

            for line in dataset.take(10):
              print([item.numpy() for item in line])
            ```

    - From TFRecrods files

        - What is TFRecord 👇🏼 ?

            - The TFRecord format `.tfrecord` is a simple format for storing a sequence of binary records.
            - TFRcords present a significant performance gain (training time) when working with large datasets
            - Since TFRecord will require you to convert your data to binary data, it would take less space on disk, less time to copy

        - How to use TFRecrod with [tf.data](http://tf.data) 👇🏼 ?

            the process is simple 😴 , just create an instance of `tf.data.TFRecordDataset` .

            ```python
            # Creates a dataset that reads all of the examples from two files.
            fsns_test_file = tf.keras.utils.get_file("fsns.tfrec", "https://storage.googleapis.com/download.tensorflow.org/data/fsns-20160927/testdata/fsns-00000-of-00001")
            ```

            ```python
            dataset = tf.data.TFRecordDataset(filenames = [fsns_test_file])
            dataset
            ```

    - Solution to commen problems

        - I have an image classfication / sentiment analysis problem ?
            - if your data is already classified into train/test data then you good to use `tf.keras.preprocessing.image.ImageDataGenerator` in case of images and `tf.keras.preprocessing.image_dataset_from_directory` in case of text

                ![Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-22_at_21.10.38.png](Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-22_at_21.10.38.png)

            - if your data fits in memory than load it into slices and pass it into `tensor_slices`
            - use a genrator and implement your python loading logic inside with the tool you desire and pass it into `from_generator`
            - TFRecords 😉

        - I have a classfication/regression task based on feature input ?
            - if you're data are in csv format then `tf.data.experimental.make_csv_dataset`  is good for you
            - if it fits in memory then keep it simple and use tensor slices
            - TFRecords or generators 😉

        - I have a problem that you all don't know about 🙃, is there a general method ?
            - Tensorslices or python generator 🙂

    .

- 2. Transforming dataset

    - Understand the basics

        ![Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-22_at_22.39.26.png](Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-22_at_22.39.26.png)

        - dataset preprocessing is preformed by the CPU
        - Tensoflow dataset load batches from the disk and do training on

            ```python
            for batch in dataset:
            		train(batch)
            ```

        - a batch is a set of blocks (1, 2 , 3 or N depeding on how big it is)
        - After loading a batch, it is generally (depends on your hardware) passed to the GPU to do training

    - Batching

        ```python
        dataset = tf.data.Dataset.range(20)
        batched_dataset = dataset.batch(4)

        for batch in batched_dataset.take(4):
          print(batch.numpy())
        ```

        ![Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Untitled.png](Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Untitled.png)

    - Repeating

        ```python
        dataset = tf.data.Dataset.range(20)
        batched_dataset = dataset.batch(4).repeat(2)

        for batch in batched_dataset.take(8):
          print(batch.numpy())
        ```

        ![Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-22_at_23.15.37.png](Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-22_at_23.15.37.png)

    - Shuffling

        ```python
        dataset = tf.data.Dataset.range(20)
        batched_dataset = dataset.shuffle(buffer_size=4).batch(4)

        for batch in batched_dataset.take(5):
          print(batch.numpy())
        ```

        ![Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-22_at_23.49.46.png](Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-22_at_23.49.46.png)

    - Mapping

        ```python
        dataset = tf.data.Dataset.range(20)
        batched_dataset = dataset.batch(4).map(lambda batch: 2 * batch)

        for batch in batched_dataset.take(5):
          print(batch.numpy())
        ```

        ![Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_00.04.25.png](Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_00.04.25.png)

    - Some Performence tips

        - Prefetching

            - Problem

                ```python
                # this example is used just for illustration 
                dataset = tf.data.Dataset.range(12)
                batched_dataset = dataset.batch(4)

                for epoch in range(2):
                	for batch in batched_dataset:
                	  print("I am learning")
                ```

                ![Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_00.41.09.png](Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_00.41.09.png)

            - Solution

                ```python
                # this example is used just for illustration 
                dataset = tf.data.Dataset.range(12)
                batched_dataset = dataset.batch(4).prefetch(1)

                for epoch in range(2):
                	for batch in batched_dataset:
                	  print("I am learning")
                ```

                ![Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_00.45.31.png](Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_00.45.31.png)

        - Prallel Transformation

            - make use of `num_parallel_calls` in `.map`, dataset creation ...etc.
            - if you're confused on how many threads you want to use `use num_parallel_calls = tf.data.AUTOTUNE`

                ![Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_01.03.19.png](Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_01.03.19.png)

                ![Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_01.05.28.png](Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_01.05.28.png)

        - Operate over big chunks

            - Problem

                ```python

                dataset = tf.data.Dataset.range(100000)
                batched_dataset = dataset.map(lambda batch: 2 * batch).batch(50000)

                for batch in batched_dataset:
                  print(batch.numpy())
                ```

                ![Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_01.15.14.png](Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_01.15.14.png)

            - Solution

                ```python
                dataset = tf.data.Dataset.range(100000)
                batched_dataset = dataset.batch(50000).map(lambda batch: 2 * batch)

                for batch in batched_dataset:
                  print(batch.numpy())
                ```

                ![Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_01.17.48.png](Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_01.17.48.png)

        - Caching to memory or to a file

            ```python

            dataset = tf.data.Dataset.range(100000)
            batched_dataset = dataset.batch(50000).cache()

            for i in range(2)
            	for batch in batched_dataset:
            	  print(batch.numpy())
            ```

            ![Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_01.24.01.png](Tensoflow%20Dataset%20API%2068d2dc5115184f4b97ab48b9a0d871d5/Screen_Shot_2021-03-23_at_01.24.01.png)