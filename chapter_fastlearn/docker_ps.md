
## ps

* 用法

	Usage: docker ps [OPTIONS]

	List containers

  	-a, --all=false       Show all containers (default shows just running)
  	--before=             Show only container created before Id or Name
  	-f, --filter=[]       Filter output based on conditions provided
  	--help=false          Print usage
  	-l, --latest=false    Show the latest created container, include non-running
  	-n=-1                 Show n last created containers, include non-running
  	--no-trunc=false      Don't truncate output
  	-q, --quiet=false     Only display numeric IDs
  	-s, --size=false      Display total file sizes
  	--since=              Show created since Id or Name, include non-running


* 例子


	$ sudo docker ps -a
	CONTAINER ID  IMAGE    COMMAND       CREATED       STATUS                      PORTS    NAMES
	b448f729a0b0  centos   "/bin/bash"   4 days ago    Exited (137) 4 days ago              pensive_wilson
	54c7b6d6632e  centos   "/bin/bash"   4 days ago    Exited (0) 3 days ago                adoring_wozniak


* 总结

-a参数列出所有状态的容器， -l列出最新创建的容器，包括停止运行状态的容器。


## kill


* 用法


	Usage: docker kill [OPTIONS] CONTAINER [CONTAINER...]

	Kill a running container using SIGKILL or a specified signal

  	--help=false         Print usage
  	-s, --signal=KILL    Signal to send to the container


* 例子


	$ sudo docker kill pensive_wilson
	pensive_wilson

这将停止该容器

* 总结

结合ps命令，可以做到kill所有正在运行的容器：

	$ sudo docker kill $(sudo docker ps -a -q)


## rm


* 用法


	Usage: docker rm [OPTIONS] CONTAINER [CONTAINER...]

	Remove one or more containers

  	-f, --force=false      Force the removal of a running container (uses SIGKILL)
  	--help=false           Print usage
  	-l, --link=false       Remove the specified link
  	-v, --volumes=false    Remove the volumes associated with the container


* 例子


	$ sudo docker rm pensive_wilson
	pensive_wilson


这将删除一个已经停止运行的容器，若容器正在运行，则将会使docker报错，停止容器再删除，或者加上-f参数强制删除（不建议）。

* 总结

类似的我们也结合ps删除所有容器：


	$ sudo docker kill $(sudo docker ps -a -q)
	...
	...
	...
	$ sudo docker rm $(sudo docker ps -a -q)
	...
	...
	...

要清空容器，首先要保证没有容器在运行。

## rmi


* 用法


	Usage: docker rmi [OPTIONS] IMAGE [IMAGE...]

	Remove one or more images

  	-f, --force=false    Force removal of the image
  	--help=false         Print usage
  	--no-prune=false     Do not delete untagged parents

* 例子


	$ sudo docker rmi centos:6.5
	...
	...
	...

* 总结

要区分rm于rmi多用法。
	与docker images命令配合来清空镜像：


	$ sudo docker rmi $(sudo docker images -a -q)

