Approach of Semi-Join Bloom Filter:

    Loading the Bloom Filter:
    In the setup phase, the Bloom filter is initialized with a specified size and hash function. The reference dataset is read from the Distributed Cache, and each key from this dataset is added to the Bloom filter.

    Mapping Phase:
    For each input record from the main dataset, the mapper extracts the key and checks its existence in the Bloom filter using the membership test.

    Filtering the Data:
    If the key exists in the Bloom filter, the corresponding record is emitted to the output. If not, the record is discarded.

    No Reducer Phase:
    Since the goal is to filter records, no reducer is required. Therefore, the number of reducers is set to zero to save computation time.

    Output Generation:
    The filtered records are written to the output directory specified in the job configuration. This approach significantly reduces the data transfer between nodes, improving efficiency.
