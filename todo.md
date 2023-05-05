
## 已完成
```c
int MPI_Gather(const void *sendbuf, int sendcount, MPI_Datatype sendtype,
               void *recvbuf, int recvcount, MPI_Datatype recvtype,
               int root, MPI_Comm comm)
int MPI_Igather(const void *sendbuf, int sendcount, MPI_Datatype sendtype,
                void *recvbuf, int recvcount, MPI_Datatype recvtype,
                int root, MPI_Comm comm, MPI_Request *request)       
int MPI_Allgather(const void *sendbuf, int sendcount, MPI_Datatype sendtype,
                void *recvbuf, int recvcount, MPI_Datatype recvtype,
                MPI_Comm comm)
int MPI_Iallgather(const void *sendbuf, int sendcount, MPI_Datatype sendtype,
                   void *recvbuf, int recvcount, MPI_Datatype recvtype,
                   MPI_Comm comm,  MPI_Request *request)
int MPI_Scatter(const void *sendbuf, int sendcount, MPI_Datatype sendtype,
                void *recvbuf, int recvcount, MPI_Datatype recvtype,
                int root, MPI_Comm comm)
int MPI_Iscatter(const void *sendbuf, int sendcount, MPI_Datatype sendtype,
                 void *recvbuf, int recvcount, MPI_Datatype recvtype,
                 int root, MPI_Comm comm, MPI_Request *request)
int MPI_Exscan(const void *sendbuf, void *recvbuf, int count,
               MPI_Datatype datatype, MPI_Op op, MPI_Comm comm)

```

## 未完成
```c


```

## IMB-RMA Benchmarks
```c
//https://www.intel.com/content/www/us/en/docs/mpi-library/user-guide-benchmarks/2021-2/imb-rma-benchmarks.html

int MPI_Put(const void *origin_addr, int origin_count, MPI_Datatype origin_datatype,
            int target_rank, MPI_Aint target_disp, int target_count,
            MPI_Datatype target_datatype, MPI_Win win)
int MPI_Get(void *origin_addr, int origin_count,
            MPI_Datatype origin_datatype, int target_rank,
            MPI_Aint target_disp, int target_count,
            MPI_Datatype target_datatype, MPI_Win win)
int MPI_Compare_and_swap(const void *origin_addr, const void *compare_addr, void *result_addr,
                         MPI_Datatype datatype, int target_rank, MPI_Aint target_disp, MPI_Win win)
int MPI_Get_accumulate(const void *origin_addr, int origin_count, MPI_Datatype origin_datatype,
                       void *result_addr, int result_count, MPI_Datatype result_datatype,
                       int target_rank, MPI_Aint target_disp, int target_count,
                       MPI_Datatype target_datatype, MPI_Op op, MPI_Win win)
int MPI_Fetch_and_op(const void *origin_addr, void *result_addr, MPI_Datatype datatype,
                     int target_rank, MPI_Aint target_disp, MPI_Op op, MPI_Win win)

int MPI_Win_flush_all(MPI_Win win)
int MPI_Win_flush(int rank, MPI_Win win)
int MPI_Win_flush_local(int rank, MPI_Win win)
```
## IMB-NBC Benchmarks
```c
//https://www.intel.com/content/www/us/en/docs/mpi-library/user-guide-benchmarks/2021-2/imb-nbc-benchmarks.html
int MPI_Iallgatherv(const void *sendbuf, int sendcount,
   	MPI_Datatype sendtype, void *recvbuf, const int recvcounts[],
   	const int displs[], MPI_Datatype recvtype, MPI_Comm comm,
           MPI_Request *request)
int MPI_Ialltoallv(const void *sendbuf, const int sendcounts[],
   	const int sdispls[], MPI_Datatype sendtype,
   	void *recvbuf, const int recvcounts[],
   	const int rdispls[], MPI_Datatype recvtype, MPI_Comm comm,
   	MPI_Request *request)
int MPI_Igatherv(const void *sendbuf, int sendcount, MPI_Datatype sendtype,
    void *recvbuf, const int recvcounts[], const int displs[], MPI_Datatype recvtype,
    int root, MPI_Comm comm, MPI_Request *request)
int MPI_Ireduce_scatter(const void *sendbuf, void *recvbuf, const int recvcounts[],
                        MPI_Datatype datatype, MPI_Op op, MPI_Comm comm, MPI_Request *request)
int MPI_Iscatterv(const void *sendbuf, const int sendcounts[], const int displs[],
	MPI_Datatype sendtype, void *recvbuf, int recvcount,
	MPI_Datatype recvtype, int root, MPI_Comm comm, MPI_Request *request)
```

## 其他 - 需要更改
```c
int MPI_Reduce_scatter(const void *sendbuf, void *recvbuf, const int recvcounts[],
                MPI_Datatype datatype, MPI_Op op, MPI_Comm comm)
int MPI_Sendrecv(const void *sendbuf, int sendcount, MPI_Datatype sendtype,
                 int dest, int sendtag, void *recvbuf, int recvcount,
                 MPI_Datatype recvtype, int source, int recvtag,
                 MPI_Comm comm,  MPI_Status *status) // 两个tag,需要更改trace_log_struct
int MPI_Alltoallv(const void *sendbuf, const int sendcounts[],
   	const int sdispls[], MPI_Datatype sendtype,
   	void *recvbuf, const int recvcounts[],
   	const int rdispls[], MPI_Datatype recvtype, MPI_Comm comm)

int MPI_Alltoallw(const void *sendbuf, const int sendcounts[],
   	const int sdispls[], const MPI_Datatype sendtypes[],
   	void *recvbuf, const int recvcounts[], const int rdispls[],
   	const MPI_Datatype recvtypes[], MPI_Comm comm)
int MPI_Ialltoallw(const void *sendbuf, const int sendcounts[],
   	const int sdispls[], const MPI_Datatype sendtypes[],
   	void *recvbuf, const int recvcounts[], const int rdispls[],
   	const MPI_Datatype recvtypes[], MPI_Comm comm,
   	MPI_Request *request)
int MPI_Gatherv(const void *sendbuf, int sendcount, MPI_Datatype sendtype,
    void *recvbuf, const int recvcounts[], const int displs[], MPI_Datatype recvtype,
    int root, MPI_Comm comm)
int MPI_Scatterv(const void *sendbuf, const int sendcounts[], const int displs[],
	MPI_Datatype sendtype, void *recvbuf, int recvcount,
	MPI_Datatype recvtype, int root, MPI_Comm comm)


```