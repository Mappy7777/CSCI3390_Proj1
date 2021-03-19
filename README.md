1. I am using the string "this_is_a_bitcoin_block_of_37881382" for all of these.

For k = 2, found 1989726188this_is_a_bitcoin_block_of_37881382,007189ff64a7746a88f8971622d75c10e8ee2264f91dfe60b86930ee248992a1 in 1 second. 100 trials.

For k = 3, found 2092314030this_is_a_bitcoin_block_of_37881382,000771c090bccd9106ca141f4f5eb99606ff1b2b227f51ef3fd84766bd5c01ef in 1 second. 1,000 trials.

For k = 4, found 938114513this_is_a_bitcoin_block_of_37881382,0000f246138fa171d621e73f621bca9291d49aeec57966ae5e4e20fb85a2059f in 1 second. 50,000 trials.

For k = 5, found 424657956this_is_a_bitcoin_block_of_37881382,00000b088e8b3bf76dc8f69aae6abcf69ca19c5a89d64634bfe226af42028089 in 1 second. 500,000 trials.

For k = 6, found 1291095249this_is_a_bitcoin_block_of_37881382,0000006c521ac09160a5e4e811fef7a20affb5c1d2203ea81ac15c14c56a32c7 in 5 seconds. 10,000,000 trials.


2. The cluster I'm using for this job (fitzpass-csci3390-cluster) has 1 master node with 2 worker nodes. Each node has 4 Intel Haswell CPUs with 15 GB of memory. 

For k = 7, found 1742212358this_is_a_bitcoin_block_of_37881382,00000001fca2067ff8a936eca5651e65bb8e0c87f7a857acfa9ac3c6f8133abd in 1878 seconds. 500,000,000 trials.

I estimated the number of trials based on the rough factor of increase that I found worked for prior trials. Initially I used 100,000,000 trials but came up with no results so I increased that to 500,000,000 and found a result.


#3.
Changing line 58 from

iter.map(x => rand.nextInt(Int.MaxValue - 1) + 1)

to

iter.map(x => nonce)

This removes the randomization aspect of it while only changing 1 line, although line 57 becomes pretty meaningless then.

In theory no one nonce is any more likely than another to produce the required prefix of 0's. So there shouldn't be any noticable difference iterating from 0 to #trials with the nonce instead of randomizing it.
