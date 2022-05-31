

## User Guide of XACC Cluster at NUS

### Registration
For researchers outside NUS, please request access through [Xilinx University Program](https://www.xilinx.com/support/university/XUP-XACC.html).

For researchers at NUS, please apply through the following link: [NUS HACC Account Registration](https://forms.gle/fvfPgJypd1sSWzHm8).

The guest account expires after __one year__ or there is no login event within __two months__. You will get a notification from NUS of this event one month in advance. If you plan to keep using the resources, please follow the instruction in the notification mail.


### Compute Node Configuration

|Host    | Boards |  Quantity | Shell Version | XRT Version | Vitis Version |
|--------|--------|-------|----------|-------------|-------------------|
| xaccnode0.d2.comp.nus.edu.sg |  Alveo U250 | 2 | xilinx_u250_xdma_201830_2 | 2.7.766 | Vitis 2020.1 |
| xaccnode1.d2.comp.nus.edu.sg |  Alveo U250 | 2 | xilinx_u250_xdma_201830_2 | 2.7.766 | Vitis 2020.1 |
| xaccnode2.d2.comp.nus.edu.sg |  Alveo U280 | 4 | xilinx_u280_xdma_201920_1 | 2.5.309 | Vitis 2019.2 |
| xaccnode3.d2.comp.nus.edu.sg |  Alveo U250 | 2 | xilinx_u250_qdma_201920_1 | 2.5.309 | Vitis 2019.2 |

### Access to the Cluster
Researchers at NUS could directly access the corresponding node with SSH: 
```shell
ssh username@xaccnodex.d2.comp.nus.edu.sg
```
Researchers outside NUS need to access a jump host (which has a public IP address) at first before accessing the servers with FPGA boards. 

__NOTE__: we highly recommand you to enable the SSH key based secure authentication. You can refer the following command.

``` shell
# make sure you already generated ssh key by ssh-keygen
# replace "your_username" to your given account
cat ~/.ssh/id_rsa.pub | ssh your_username@xacchead.d2.comp.nus.edu.sg "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys && chmod 700 ~/.ssh  && chmod 600 ~/.ssh/authorized_keys" 

```


### Setting the FPGA Environment

XACC clusters support the __Vitis Design Flow__. Benefiting from XRT environments and C/C++ based HLS tools, FPGA developlors can easy test their code in real hardware, and algorithm designers can ignore the hardware details. If you want to evaluate some RTL modules, we suggest you try the  mix programming with Vitis following [this](https://www.xilinx.com/developer/articles/Integrating-optimized-RTL-Kernels-into-Accelerated-Applications-using-Vitis.html)
and [examples](https://github.com/Xilinx/Vitis_Accel_Examples/tree/master/rtl_kernels). 


Users should then use the following command to setup the environment:
```shell
# Set XRT Environment
source /opt/xilinx/xrt/setup.sh
# Set Vitis Environment, for the node installed Vitis 2020.1
source  /opt/Xilinx/Vitis/2020.1/settings64.sh

# Set Vitis Environment, for the node installed Vitis 2020.2
source  /opt/Xilinx/Vitis/2020.2/settings64.sh

```

### Shared Storage

```/data``` is a shared path in all compute nodes for users to store insensitive data. 
Please keep your data size within 50GB.

### Support

#### Cluster environment:
If you need help (e.g., software installation), you can submit issues in [here](https://github.com/XACCNUS/Cluster/issues/new).

You also can join our Telegram Group ([HACC@NUS Forum](https://t.me/joinchat/E3BBIyP9u16fTmmH)) for emergency help (e.g., registration problems).

#### Password reset:
In case you forgot your account's password, you can email xacc.nus.user@gmail.com with the following information 

Subject: Reset password
Context:  Account: your_username


### Acknowledgement
We would like to thank [Xilinx](https://www.xilinx.com/) for the hardware donation.
