# Configure a Linux server on AWS

If you do not have access to a computer running Linux \(or VirtualBox\), you can use Amazon Web Services \(AWS\) to create a cloud-based virtual machine running Linux for free. To do so, please follow the steps below:

* Go to [Amazon Web Services \(AWS\)](https://aws.amazon.com/) and create a \(free\) account if you do not have one already.
* Go to the _AWS Management Console_.
* Go to the _EC2 Dashboard_.

![](../../.gitbook/assets/AMI.png)

* If you already have a running instance, go to step 9.
* We must first make sure to get enough harddrive space \(at least 24GB\). Click on _Volumes_.

![](../../.gitbook/assets/volumes.png)

* Under _Actions_, select _Modify Volume_.

![](../../.gitbook/assets/volume_actions.png)

* In the _Modify Volume_ dialog, select a size of 24 and click _Modify_, then confirm in the next dialog.

![](../../.gitbook/assets/modify_volume.png)

* Go back to the _EC2 Dashboard_.

![](../../.gitbook/assets/dashboard.png)

* Go to _Launch Instance_.

![](../../.gitbook/assets/launch_instance.png)

* As Amazon Machine Image, choose _Amazon Linux 2 \(HVM\), SSD Volume Type_, 64-bit \(x86\).

![](../../.gitbook/assets/AMI.png)

* As Instance Type, choose _t2.medium_, then click _Review and Launch_ and finally _Launch_ on the next screen.

![](../../.gitbook/assets/Instance_Type.png)

* Create a key pair \(or use an existing one\).

![](../../.gitbook/assets/key_pair.png)

* _Connect_ to your instance.

![](../../.gitbook/assets/connect.png)

* You can use the _EC2 Instance Connect_ connection method.

![](../../.gitbook/assets/connect2.png)



{% hint style="info" %}
QUESTIONS AND FEEDBACK

  
If you have any questions and suggestions while taking the lessons please feel free to ask in the [forum](https://forum.cardano.org/c/english/operators-talk/119) and we will respond as soon as possible.
{% endhint %}

Congratulations! You have now access to a machine running Linux.

