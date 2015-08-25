
## pause

* 用法


	Usage: docker pause [OPTIONS] CONTAINER [CONTAINER...]

	Pause all processes within a container

  	--help=false       Print usage


* 例子


	$ sudo docker pauese hopeful_feynman
	hopeful_feynman
	CONTAINER ID    IMAGE     COMMAND      CREATED         STATUS                 PORTS       NAMES
	c9a12157fed7    centos    "/bin/bash"  9 minutes ago   Up 9 minutes (Paused)              hopeful_feynman


使容器内进程暂停

## unpause


* 用法


	Usage: docker unpause [OPTIONS] CONTAINER [CONTAINER...]

	Unpause all processes within a container

  	--help=false       Print usage


* 例子


	$ sudo docker pauese hopeful_feynman
	hopeful_feynman
恢复暂停


