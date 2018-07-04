# bwa-test
bwa is a kind of bioinformatic analysis application

# test steps

1.  download from baidu yun disk

filename : hwfssz4_test100_bwa-assess_16.tar.bz2a[a-d] 

比对一下校验码，以防止文件在传输过程中出错。
```bash
# md5sum *bz2*
ad59f861f15319da56c9aa02bbd15c50  hwfssz4_test100_bwa-assess_16.tar.bz2aa
745a7474a57eb7967731115a6606c404  hwfssz4_test100_bwa-assess_16.tar.bz2ab
c1dde8866a222ee98664efbcb4e8a3f1  hwfssz4_test100_bwa-assess_16.tar.bz2ac
eafa7439bf2efccde144647ca82e9539  hwfssz4_test100_bwa-assess_16.tar.bz2ad
```


文件解压之后30G大小，在Openstack平台，找一个干净的计算节点，满足最小条件: CPU core >=24, memory >=120G
在其他创建2个KVM VM, 以物理机32个cpu core, 128G内存为例，则KVM VM 的flavor 为16 vcpu ,64G memory. 

跑2个test case:

case1: 只在一个vm中跑bwa test, 跑完的时间为t1
case2: 在2个vm中同时跑bwa test,跑完的时间为t2 

一般来讲， t2> t1, 计算 (t2-t1)/t1,该值越小越好。


2. how to run bwa test ? 

## 将解压后的2个文件夹放入对应的目录 

```bash
mkdir /hwfssz4/test100/bwa-assess
mkdir /share/app/
mv bwa-0.7.12  /share/app
mv 16  /hwfssz4/test100/bwa-assess
```

## 调整参数，跑脚本 

这里还是以32 cpu core的compute node为例,确保bwa.sh脚本中的线程数`-t 16` 等于作为vm的vcpu core数量 
```
/share/app/bwa-0.7.12/bwa mem -t 16
```


```bash
[root@test-1 ~]# cd /hwfssz4/test100/bwa-assess/16
[root@test-1 16]# ls
170301_X488_FCHFC3MALXX_L6_wHAXPI043638-8_1.fq.gz  bwa.sh      realtime   ref
170301_X488_FCHFC3MALXX_L6_wHAXPI043638-8_2.fq.gz  huawei.sam  realtime2  runtime.record
[root@test-1 16]# cat bwa.sh 
#!/bin/bash
echo "-----------------" >> runtime.record
echo "start at:" `date` >> runtime.record 
/share/app/bwa-0.7.12/bwa mem -t 16 -M -Y -R "@RG\tID:170205_I44_CL100013600_L1_WHHUMoahAAAASAAZebra-47\tPL:COMPLETE\tPU:
170205_I44_CL100013600_L1\tLB:XWHHUMoahAAAASAAZebra-47\tSM:XWH\tCN:BGI" /hwfssz4/test100/bwa-assess/16/ref/hg19.fasta /hwfssz4/test100/bwa-assess/16/170301_X488_FCHFC3MALXX_L6_wHAXPI043638-8_1.fq.gz /hwfssz4/test100/bwa-assess/16/170301_X488_FCHFC3MALXX_L6_wHAXPI043638-8_2.fq.gz > /hwfssz4/test100/bwa-assess/16/huawei.samecho "end at:" `date` >> runtime.record 

```
run bwa.sh , wait until it finish,then check runtime.record.


