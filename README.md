networking-qos
==============

Daemonset with some tc rules to verify influence on metrics:
 - node_ethtool_bw_in_allowance_exceeded
 - node_ethtool_bw_out_allowance_exceeded
 - node_ethtool_pps_allowance_exceeded

This approach is mentioned in AWS Knowledge Center[^1]
  - Queuing disciplines (qdiscs): qdiscs are responsible for packet scheduling and optional shaping. Some qdiscs,
    such as fq, help smooth out traffic bursts from individual flows. For more information, see the Traffic Control
    (TC) manual page.

This Solution leverage linux traffic-control (tc)[^2] with htb[^3] and fq_codel[^4]

To monitor this traffic on host, use bmon[^5]:

  ```
  sudo yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
  sudo yum install -y bmon
  ```

Resources:
  - https://wiki.gentoo.org/wiki/Traffic_shaping

[^1]: https://repost.aws/knowledge-center/ec2-instance-exceeding-network-limits
[^2]: https://man7.org/linux/man-pages/man8/tc.8.html
[^3]: https://man7.org/linux/man-pages/man8/tc-htb.8.html
[^4]: https://man7.org/linux/man-pages/man8/tc-fq_codel.8.html
[^5]: https://github.com/tgraf/bmon
