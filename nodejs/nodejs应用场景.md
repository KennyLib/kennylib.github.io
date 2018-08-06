# 应用场景

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

* [应用场景](#应用场景)
	* [I/O密集型](#io密集型)
	* [是否不擅长](#是否不擅长)

<!-- /code_chunk_output -->

## I/O密集型

Node面向网络且擅长并行I/O，能够有效地组织起更多的硬件资源，从而提供更多好的服务。
I/O秘籍的优势主要在于Node利用时间循环的处理能力，而不是在启动每一个线程为每一个请求服务，资源占用极少。

## 是否不擅长CPU密集型业务