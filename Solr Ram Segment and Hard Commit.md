## During Hard Commit
1. The tlog is truncated: A new tlog is started. (Disk IO involved)
2. The current index segment (in Ram) is closed and flushed. (Disk IO involved)

## Between two hard commits:
1. new added documents are hosted in Ram buffer first. (defined in solrconfig, ramBufferSizeMB. No Disk IO involved)
I assume this buffer actually host an open segment in ram, am I right?
2. What will happen when the ram buffer is full and the time of autocommit is not reached yet? Will Solr flush the segment in ram to disk anyway?
3. The <maxIndexingThreads> controls how many threads will be used to add, delete docs to and from Ram segment. The thread for flusing Ram segment to disk is also from here.
