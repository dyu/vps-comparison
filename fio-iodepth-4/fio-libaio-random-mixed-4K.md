# fio results (all on ubuntu 16.04 x64)
```
# random read/write
fio --filename=test4K-rw-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randrw --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G --rwmixread=40
```

## aws ec2 micro - 990M
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            488M     0  488M   0% /dev
tmpfs           100M   11M   89M  11% /run
/dev/xvda1      7.7G  2.2G  5.6G  28% /
tmpfs           496M     0  496M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           496M     0  496M   0% /sys/fs/cgroup
tmpfs           100M     0  100M   0% /run/user/901
```

*rw*
```
./fio --filename=test4K-rw-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randrw --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G --rwmixread=40
myjob: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [m(1)][1.3%][r=4912KiB/s,w=7339KiB/s][r=1228,w=1834 IOPS][eta 03mJobs: 1 (f=1): [m(1)][1.5%][r=4900KiB/s,w=7296KiB/s][r=1225,w=1824 IOPS][eta 04mJobs: 1 (f=1): [m(1)][1.8%][r=4848KiB/s,w=7267KiB/s][r=1212,w=1816 IOPS][eta 04mJobs: 1 (f=1): [m(1)][2.1%][r=4872KiB/s,w=7495KiB/s][r=1218,w=1873 IOPS][eta 04mJobs: 1 (f=1): [m(1)][2.3%][r=4932KiB/s,w=7219KiB/s][r=1233,w=1804 IOPS][eta 04mJobs: 1 (f=1): [m(1)][2.7%][r=4988KiB/s,w=7420KiB/s][r=1247,w=1855 IOPS][eta 04mJobs: 1 (f=1): [m(1)][3.0%][r=4960KiB/s,w=7291KiB/s][r=1240,w=1822 IOPS][eta 04mJobs: 1 (f=1): [m(1)][3.3%][r=4976KiB/s,w=7271KiB/s][r=1244,w=1817 IOPS][eta 04mJobs: 1 (f=1): [m(1)][3.7%][r=4892KiB/s,w=7356KiB/s][r=1223,w=1839 IOPS][eta 04mJobs: 1 (f=1): [m(1)][4.0%][r=4808KiB/s,w=7439KiB/s][r=1202,w=1859 IOPS][eta 04mJobs: 1 (f=1): [m(1)][4.3%][r=4820KiB/s,w=7427KiB/s][r=1205,w=1856 IOPS][eta 04mJobs: 1 (f=1): [m(1)][4.7%][r=4940KiB/s,w=7307KiB/s][r=1235,w=1826 IOPS][eta 04mJobs: 1 (f=1): [m(1)][5.0%][r=4792KiB/s,w=7456KiB/s][r=1198,w=1864 IOPS][eta 04mJobs: 1 (f=1): [m(1)][5.3%][r=4904KiB/s,w=7347KiB/s][r=1226,w=1836 IOPS][eta 04mJobs: 1 (f=1): [m(1)][5.6%][r=4956KiB/s,w=7291KiB/s][r=1239,w=1822 IOPS][eta 04mJobs: 1 (f=1): [m(1)][6.0%][r=4844KiB/s,w=7247KiB/s][r=1211,w=1811 IOPS][eta 04mJobs: 1 (f=1): [m(1)][6.3%][r=4936KiB/s,w=7288KiB/s][r=1234,w=1822 IOPS][eta 04mJobs: 1 (f=1): [m(1)][6.6%][r=4992KiB/s,w=7439KiB/s][r=1248,w=1859 IOPS][eta 04mJobs: 1 (f=1): [m(1)][7.0%][r=4868KiB/s,w=7379KiB/s][r=1217,w=1844 IOPS][eta 04mJobs: 1 (f=1): [m(1)][7.3%][r=4704KiB/s,w=7544KiB/s][r=1176,w=1886 IOPS][eta 04mJobs: 1 (f=1): [m(1)][7.6%][r=4768KiB/s,w=7475KiB/s][r=1192,w=1868 IOPS][eta 04mJobs: 1 (f=1): [m(1)][8.0%][r=4964KiB/s,w=7231KiB/s][r=1241,w=1807 IOPS][eta 04mJobs: 1 (f=1): [m(1)][8.3%][r=4812KiB/s,w=7383KiB/s][r=1203,w=1845 IOPS][eta 04mJobs: 1 (f=1): [m(1)][8.6%][r=5036KiB/s,w=7172KiB/s][r=1259,w=1793 IOPS][eta 04mJobs: 1 (f=1): [m(1)][9.0%][r=4788KiB/s,w=7175KiB/s][r=1197,w=1793 IOPS][eta 04mJobs: 1 (f=1): [m(1)][9.3%][r=4872KiB/s,w=7599KiB/s][r=1218,w=1899 IOPS][eta 04mJobs: 1 (f=1): [m(1)][9.6%][r=4980KiB/s,w=7331KiB/s][r=1245,w=1832 IOPS][eta 04mJobs: 1 (f=1): [m(1)][10.0%][r=4988KiB/s,w=7144KiB/s][r=1247,w=1786 IOPS][eta 04Jobs: 1 (f=1): [m(1)][10.3%][r=4872KiB/s,w=7435KiB/s][r=1218,w=1858 IOPS][eta 04Jobs: 1 (f=1): [m(1)][10.6%][r=4744KiB/s,w=6938KiB/s][r=1186,w=1734 IOPS][eta 04Jobs: 1 (f=1): [m(1)][11.0%][r=5172KiB/s,w=7692KiB/s][r=1293,w=1923 IOPS][eta 04Jobs: 1 (f=1): [m(1)][11.3%][r=4964KiB/s,w=7287KiB/s][r=1241,w=1821 IOPS][eta 04Jobs: 1 (f=1): [m(1)][11.6%][r=4684KiB/s,w=7579KiB/s][r=1171,w=1894 IOPS][eta 04Jobs: 1 (f=1): [m(1)][12.0%][r=5208KiB/s,w=7028KiB/s][r=1302,w=1757 IOPS][eta 04Jobs: 1 (f=1): [m(1)][12.3%][r=4804KiB/s,w=7443KiB/s][r=1201,w=1860 IOPS][eta 04Jobs: 1 (f=1): [m(1)][12.6%][r=4912KiB/s,w=7335KiB/s][r=1228,w=1833 IOPS][eta 04Jobs: 1 (f=1): [m(1)][13.0%][r=4696KiB/s,w=7555KiB/s][r=1174,w=1888 IOPS][eta 04Jobs: 1 (f=1): [m(1)][13.3%][r=5000KiB/s,w=7248KiB/s][r=1250,w=1812 IOPS][eta 04Jobs: 1 (f=1): [m(1)][13.6%][r=4796KiB/s,w=7451KiB/s][r=1199,w=1862 IOPS][eta 04Jobs: 1 (f=1): [m(1)][14.0%][r=5029KiB/s,w=7223KiB/s][r=1257,w=1805 IOPS][eta 04Jobs: 1 (f=1): [m(1)][14.3%][r=4896KiB/s,w=7351KiB/s][r=1224,w=1837 IOPS][eta 04Jobs: 1 (f=1): [m(1)][14.6%][r=5048KiB/s,w=7176KiB/s][r=1262,w=1794 IOPS][eta 04Jobs: 1 (f=1): [m(1)][15.0%][r=4928KiB/s,w=7223KiB/s][r=1232,w=1805 IOPS][eta 04Jobs: 1 (f=1): [m(1)][15.3%][r=4748KiB/s,w=7587KiB/s][r=1187,w=1896 IOPS][eta 04Jobs: 1 (f=1): [m(1)][15.6%][r=4980KiB/s,w=7299KiB/s][r=1245,w=1824 IOPS][eta 04Jobs: 1 (f=1): [m(1)][15.9%][r=4792KiB/s,w=7456KiB/s][r=1198,w=1864 IOPS][eta 04Jobs: 1 (f=1): [m(1)][16.3%][r=4968KiB/s,w=7247KiB/s][r=1242,w=1811 IOPS][eta 04Jobs: 1 (f=1): [m(1)][16.6%][r=4780KiB/s,w=7363KiB/s][r=1195,w=1840 IOPS][eta 04Jobs: 1 (f=1): [m(1)][16.9%][r=4644KiB/s,w=7639KiB/s][r=1161,w=1909 IOPS][eta 04Jobs: 1 (f=1): [m(1)][17.3%][r=4920KiB/s,w=7348KiB/s][r=1230,w=1837 IOPS][eta 04Jobs: 1 (f=1): [m(1)][17.6%][r=4884KiB/s,w=7375KiB/s][r=1221,w=1843 IOPS][eta 04Jobs: 1 (f=1): [m(1)][17.9%][r=4888KiB/s,w=7435KiB/s][r=1222,w=1858 IOPS][eta 04Jobs: 1 (f=1): [m(1)][18.3%][r=4712KiB/s,w=7539KiB/s][r=1178,w=1884 IOPS][eta 04Jobs: 1 (f=1): [m(1)][18.6%][r=4844KiB/s,w=7404KiB/s][r=1211,w=1851 IOPS][eta 04Jobs: 1 (f=1): [m(1)][18.9%][r=4976KiB/s,w=7255KiB/s][r=1244,w=1813 IOPS][eta 04Jobs: 1 (f=1): [m(1)][19.3%][r=4824KiB/s,w=7251KiB/s][r=1206,w=1812 IOPS][eta 04Jobs: 1 (f=1): [m(1)][19.6%][r=4964KiB/s,w=7328KiB/s][r=1241,w=1832 IOPS][eta 04Jobs: 1 (f=1): [m(1)][19.9%][r=4984KiB/s,w=7399KiB/s][r=1246,w=1849 IOPS][eta 04Jobs: 1 (f=1): [m(1)][20.3%][r=4832KiB/s,w=7411KiB/s][r=1208,w=1852 IOPS][eta 04Jobs: 1 (f=1): [m(1)][20.6%][r=5025KiB/s,w=7207KiB/s][r=1256,w=1801 IOPS][eta 03Jobs: 1 (f=1): [m(1)][20.9%][r=4868KiB/s,w=7264KiB/s][r=1217,w=1816 IOPS][eta 03Jobs: 1 (f=1): [m(1)][21.3%][r=5069KiB/s,w=7287KiB/s][r=1267,w=1821 IOPS][eta 03Jobs: 1 (f=1): [m(1)][21.6%][r=5177KiB/s,w=7099KiB/s][r=1294,w=1774 IOPS][eta 03Jobs: 1 (f=1): [m(1)][21.9%][r=4944KiB/s,w=7303KiB/s][r=1236,w=1825 IOPS][eta 03Jobs: 1 (f=1): [m(1)][22.3%][r=4968KiB/s,w=7280KiB/s][r=1242,w=1820 IOPS][eta 03Jobs: 1 (f=1): [m(1)][22.6%][r=4984KiB/s,w=7267KiB/s][r=1246,w=1816 IOPS][eta 03Jobs: 1 (f=1): [m(1)][22.9%][r=4864KiB/s,w=7383KiB/s][r=1216,w=1845 IOPS][eta 03Jobs: 1 (f=1): [m(1)][23.3%][r=4892KiB/s,w=7355KiB/s][r=1223,w=1838 IOPS][eta 03Jobs: 1 (f=1): [m(1)][23.6%][r=4816KiB/s,w=7300KiB/s][r=1204,w=1825 IOPS][eta 03Jobs: 1 (f=1): [m(1)][23.9%][r=4944KiB/s,w=7411KiB/s][r=1236,w=1852 IOPS][eta 03Jobs: 1 (f=1): [m(1)][24.3%][r=4952KiB/s,w=7199KiB/s][r=1238,w=1799 IOPS][eta 03Jobs: 1 (f=1): [m(1)][24.6%][r=4684KiB/s,w=7652KiB/s][r=1171,w=1913 IOPS][eta 03Jobs: 1 (f=1): [m(1)][24.9%][r=4720KiB/s,w=7563KiB/s][r=1180,w=1890 IOPS][eta 03Jobs: 1 (f=1): [m(1)][25.2%][r=4868KiB/s,w=7379KiB/s][r=1217,w=1844 IOPS][eta 03Jobs: 1 (f=1): [m(1)][25.6%][r=4776KiB/s,w=7471KiB/s][r=1194,w=1867 IOPS][eta 03Jobs: 1 (f=1): [m(1)][25.9%][r=4856KiB/s,w=7392KiB/s][r=1214,w=1848 IOPS][eta 03Jobs: 1 (f=1): [m(1)][26.2%][r=4824KiB/s,w=7423KiB/s][r=1206,w=1855 IOPS][eta 03Jobs: 1 (f=1): [m(1)][26.6%][r=4876KiB/s,w=7371KiB/s][r=1219,w=1842 IOPS][eta 03Jobs: 1 (f=1): [m(1)][26.9%][r=4896KiB/s,w=7355KiB/s][r=1224,w=1838 IOPS][eta 03Jobs: 1 (f=1): [m(1)][27.2%][r=4852KiB/s,w=7396KiB/s][r=1213,w=1849 IOPS][eta 03Jobs: 1 (f=1): [m(1)][27.6%][r=4884KiB/s,w=7363KiB/s][r=1221,w=1840 IOPS][eta 03Jobs: 1 (f=1): [m(1)][27.9%][r=4920KiB/s,w=7327KiB/s][r=1230,w=1831 IOPS][eta 03Jobs: 1 (f=1): [m(1)][28.2%][r=4880KiB/s,w=7367KiB/s][r=1220,w=1841 IOPS][eta 03Jobs: 1 (f=1): [m(1)][28.6%][r=4912KiB/s,w=7276KiB/s][r=1228,w=1819 IOPS][eta 03Jobs: 1 (f=1): [m(1)][28.9%][r=4712KiB/s,w=7375KiB/s][r=1178,w=1843 IOPS][eta 03Jobs: 1 (f=1): [m(1)][29.2%][r=4820KiB/s,w=7607KiB/s][r=1205,w=1901 IOPS][eta 03Jobs: 1 (f=1): [m(1)][29.6%][r=5116KiB/s,w=7060KiB/s][r=1279,w=1765 IOPS][eta 03Jobs: 1 (f=1): [m(1)][29.9%][r=5013KiB/s,w=7267KiB/s][r=1253,w=1816 IOPS][eta 03Jobs: 1 (f=1): [m(1)][30.2%][r=4844KiB/s,w=7479KiB/s][r=1211,w=1869 IOPS][eta 03Jobs: 1 (f=1): [m(1)][30.6%][r=5049KiB/s,w=7195KiB/s][r=1262,w=1798 IOPS][eta 03Jobs: 1 (f=1): [m(1)][30.9%][r=4868KiB/s,w=7384KiB/s][r=1217,w=1846 IOPS][eta 03Jobs: 1 (f=1): [m(1)][31.2%][r=4924KiB/s,w=7323KiB/s][r=1231,w=1830 IOPS][eta 03Jobs: 1 (f=1): [m(1)][31.6%][r=4908KiB/s,w=7343KiB/s][r=1227,w=1835 IOPS][eta 03Jobs: 1 (f=1): [m(1)][31.9%][r=5033KiB/s,w=7215KiB/s][r=1258,w=1803 IOPS][eta 03Jobs: 1 (f=1): [m(1)][32.2%][r=5012KiB/s,w=7236KiB/s][r=1253,w=1809 IOPS][eta 03Jobs: 1 (f=1): [m(1)][32.6%][r=4824KiB/s,w=7423KiB/s][r=1206,w=1855 IOPS][eta 03Jobs: 1 (f=1): [m(1)][32.9%][r=4976KiB/s,w=7179KiB/s][r=1244,w=1794 IOPS][eta 03Jobs: 1 (f=1): [m(1)][33.2%][r=5152KiB/s,w=7160KiB/s][r=1288,w=1790 IOPS][eta 03Jobs: 1 (f=1): [m(1)][33.6%][r=4904KiB/s,w=7371KiB/s][r=1226,w=1842 IOPS][eta 03Jobs: 1 (f=1): [m(1)][33.9%][r=4852KiB/s,w=7395KiB/s][r=1213,w=1848 IOPS][eta 03Jobs: 1 (f=1): [m(1)][34.2%][r=4812KiB/s,w=7436KiB/s][r=1203,w=1859 IOPS][eta 03Jobs: 1 (f=1): [m(1)][34.6%][r=5001KiB/s,w=7243KiB/s][r=1250,w=1810 IOPS][eta 03Jobs: 1 (f=1): [m(1)][34.9%][r=4876KiB/s,w=7379KiB/s][r=1219,w=1844 IOPS][eta 03Jobs: 1 (f=1): [m(1)][35.2%][r=5013KiB/s,w=7231KiB/s][r=1253,w=1807 IOPS][eta 03Jobs: 1 (f=1): [m(1)][35.5%][r=4836KiB/s,w=7276KiB/s][r=1209,w=1819 IOPS][eta 03Jobs: 1 (f=1): [m(1)][35.9%][r=5085KiB/s,w=7255KiB/s][r=1271,w=1813 IOPS][eta 03Jobs: 1 (f=1): [m(1)][36.2%][r=4996KiB/s,w=7299KiB/s][r=1249,w=1824 IOPS][eta 03Jobs: 1 (f=1): [m(1)][36.5%][r=4992KiB/s,w=7259KiB/s][r=1248,w=1814 IOPS][eta 03Jobs: 1 (f=1): [m(1)][36.9%][r=5044KiB/s,w=7204KiB/s][r=1261,w=1801 IOPS][eta 03Jobs: 1 (f=1): [m(1)][37.2%][r=4928KiB/s,w=7319KiB/s][r=1232,w=1829 IOPS][eta 03Jobs: 1 (f=1): [m(1)][37.5%][r=4800KiB/s,w=7359KiB/s][r=1200,w=1839 IOPS][eta 03Jobs: 1 (f=1): [m(1)][37.9%][r=4964KiB/s,w=7335KiB/s][r=1241,w=1833 IOPS][eta 03Jobs: 1 (f=1): [m(1)][38.2%][r=4980KiB/s,w=7304KiB/s][r=1245,w=1826 IOPS][eta 03Jobs: 1 (f=1): [m(1)][38.5%][r=4724KiB/s,w=7523KiB/s][r=1181,w=1880 IOPS][eta 03Jobs: 1 (f=1): [m(1)][38.9%][r=4984KiB/s,w=7259KiB/s][r=1246,w=1814 IOPS][eta 03Jobs: 1 (f=1): [m(1)][39.2%][r=4968KiB/s,w=7280KiB/s][r=1242,w=1820 IOPS][eta 03Jobs: 1 (f=1): [m(1)][39.5%][r=5037KiB/s,w=7211KiB/s][r=1259,w=1802 IOPS][eta 03Jobs: 1 (f=1): [m(1)][39.9%][r=5093KiB/s,w=7155KiB/s][r=1273,w=1788 IOPS][eta 03Jobs: 1 (f=1): [m(1)][40.2%][r=4796KiB/s,w=7451KiB/s][r=1199,w=1862 IOPS][eta 03Jobs: 1 (f=1): [m(1)][40.5%][r=4868KiB/s,w=7340KiB/s][r=1217,w=1835 IOPS][eta 02Jobs: 1 (f=1): [m(1)][40.9%][r=4828KiB/s,w=7411KiB/s][r=1207,w=1852 IOPS][eta 02Jobs: 1 (f=1): [m(1)][41.2%][r=4936KiB/s,w=7363KiB/s][r=1234,w=1840 IOPS][eta 02Jobs: 1 (f=1): [m(1)][41.5%][r=4928KiB/s,w=7316KiB/s][r=1232,w=1829 IOPS][eta 02Jobs: 1 (f=1): [m(1)][41.9%][r=4816KiB/s,w=7435KiB/s][r=1204,w=1858 IOPS][eta 02Jobs: 1 (f=1): [m(1)][42.2%][r=4888KiB/s,w=7363KiB/s][r=1222,w=1840 IOPS][eta 02Jobs: 1 (f=1): [m(1)][42.5%][r=4836KiB/s,w=7411KiB/s][r=1209,w=1852 IOPS][eta 02Jobs: 1 (f=1): [m(1)][42.9%][r=4840KiB/s,w=7408KiB/s][r=1210,w=1852 IOPS][eta 02Jobs: 1 (f=1): [m(1)][43.2%][r=5017KiB/s,w=7227KiB/s][r=1254,w=1806 IOPS][eta 02Jobs: 1 (f=1): [m(1)][43.5%][r=4840KiB/s,w=7411KiB/s][r=1210,w=1852 IOPS][eta 02Jobs: 1 (f=1): [m(1)][43.9%][r=4772KiB/s,w=7475KiB/s][r=1193,w=1868 IOPS][eta 02Jobs: 1 (f=1): [m(1)][44.2%][r=4692KiB/s,w=7268KiB/s][r=1173,w=1817 IOPS][eta 02Jobs: 1 (f=1): [m(1)][44.5%][r=4860KiB/s,w=7679KiB/s][r=1215,w=1919 IOPS][eta 02Jobs: 1 (f=1): [m(1)][44.9%][r=4908KiB/s,w=7339KiB/s][r=1227,w=1834 IOPS][eta 02Jobs: 1 (f=1): [m(1)][45.2%][r=4784KiB/s,w=7307KiB/s][r=1196,w=1826 IOPS][eta 02Jobs: 1 (f=1): [m(1)][45.5%][r=5052KiB/s,w=7276KiB/s][r=1263,w=1819 IOPS][eta 02Jobs: 1 (f=1): [m(1)][45.8%][r=4908KiB/s,w=7419KiB/s][r=1227,w=1854 IOPS][eta 02Jobs: 1 (f=1): [m(1)][46.2%][r=4868KiB/s,w=7375KiB/s][r=1217,w=1843 IOPS][eta 02Jobs: 1 (f=1): [m(1)][46.5%][r=4936KiB/s,w=7311KiB/s][r=1234,w=1827 IOPS][eta 02Jobs: 1 (f=1): [m(1)][46.8%][r=5160KiB/s,w=7092KiB/s][r=1290,w=1773 IOPS][eta 02Jobs: 1 (f=1): [m(1)][47.2%][r=4852KiB/s,w=7395KiB/s][r=1213,w=1848 IOPS][eta 02Jobs: 1 (f=1): [m(1)][47.5%][r=4884KiB/s,w=7363KiB/s][r=1221,w=1840 IOPS][eta 02Jobs: 1 (f=1): [m(1)][47.8%][r=4656KiB/s,w=7459KiB/s][r=1164,w=1864 IOPS][eta 02Jobs: 1 (f=1): [m(1)][48.2%][r=5120KiB/s,w=7264KiB/s][r=1280,w=1816 IOPS][eta 02Jobs: 1 (f=1): [m(1)][48.5%][r=4944KiB/s,w=7303KiB/s][r=1236,w=1825 IOPS][eta 02Jobs: 1 (f=1): [m(1)][48.8%][r=5013KiB/s,w=7227KiB/s][r=1253,w=1806 IOPS][eta 02Jobs: 1 (f=1): [m(1)][49.2%][r=4988KiB/s,w=7196KiB/s][r=1247,w=1799 IOPS][eta 02Jobs: 1 (f=1): [m(1)][49.5%][r=4832KiB/s,w=7435KiB/s][r=1208,w=1858 IOPS][eta 02Jobs: 1 (f=1): [m(1)][49.8%][r=4948KiB/s,w=7335KiB/s][r=1237,w=1833 IOPS][eta 02Jobs: 1 (f=1): [m(1)][50.2%][r=4840KiB/s,w=7416KiB/s][r=1210,w=1854 IOPS][eta 02Jobs: 1 (f=1): [m(1)][50.5%][r=4976KiB/s,w=7271KiB/s][r=1244,w=1817 IOPS][eta 02Jobs: 1 (f=1): [m(1)][50.8%][r=5037KiB/s,w=7215KiB/s][r=1259,w=1803 IOPS][eta 02Jobs: 1 (f=1): [m(1)][51.2%][r=4780KiB/s,w=7467KiB/s][r=1195,w=1866 IOPS][eta 02Jobs: 1 (f=1): [m(1)][51.5%][r=4756KiB/s,w=7492KiB/s][r=1189,w=1873 IOPS][eta 02Jobs: 1 (f=1): [m(1)][51.8%][r=4884KiB/s,w=7363KiB/s][r=1221,w=1840 IOPS][eta 02Jobs: 1 (f=1): [m(1)][52.2%][r=4936KiB/s,w=7311KiB/s][r=1234,w=1827 IOPS][eta 02Jobs: 1 (f=1): [m(1)][52.5%][r=4840KiB/s,w=7407KiB/s][r=1210,w=1851 IOPS][eta 02Jobs: 1 (f=1): [m(1)][52.8%][r=4684KiB/s,w=7564KiB/s][r=1171,w=1891 IOPS][eta 02Jobs: 1 (f=1): [m(1)][53.2%][r=5025KiB/s,w=7227KiB/s][r=1256,w=1806 IOPS][eta 02Jobs: 1 (f=1): [m(1)][53.5%][r=4788KiB/s,w=7459KiB/s][r=1197,w=1864 IOPS][eta 02Jobs: 1 (f=1): [m(1)][53.8%][r=4940KiB/s,w=7308KiB/s][r=1235,w=1827 IOPS][eta 02Jobs: 1 (f=1): [m(1)][54.2%][r=5021KiB/s,w=7155KiB/s][r=1255,w=1788 IOPS][eta 02Jobs: 1 (f=1): [m(1)][54.5%][r=4968KiB/s,w=7199KiB/s][r=1242,w=1799 IOPS][eta 02Jobs: 1 (f=1): [m(1)][54.8%][r=5097KiB/s,w=7199KiB/s][r=1274,w=1799 IOPS][eta 02Jobs: 1 (f=1): [m(1)][55.1%][r=4828KiB/s,w=7468KiB/s][r=1207,w=1867 IOPS][eta 02Jobs: 1 (f=1): [m(1)][55.5%][r=4968KiB/s,w=7331KiB/s][r=1242,w=1832 IOPS][eta 02Jobs: 1 (f=1): [m(1)][55.8%][r=4852KiB/s,w=7399KiB/s][r=1213,w=1849 IOPS][eta 02Jobs: 1 (f=1): [m(1)][56.1%][r=4664KiB/s,w=7584KiB/s][r=1166,w=1896 IOPS][eta 02Jobs: 1 (f=1): [m(1)][56.5%][r=4956KiB/s,w=7291KiB/s][r=1239,w=1822 IOPS][eta 02Jobs: 1 (f=1): [m(1)][56.8%][r=4884KiB/s,w=7363KiB/s][r=1221,w=1840 IOPS][eta 02Jobs: 1 (f=1): [m(1)][57.1%][r=4852KiB/s,w=7395KiB/s][r=1213,w=1848 IOPS][eta 02Jobs: 1 (f=1): [m(1)][57.5%][r=4932KiB/s,w=7320KiB/s][r=1233,w=1830 IOPS][eta 02Jobs: 1 (f=1): [m(1)][57.8%][r=4820KiB/s,w=7427KiB/s][r=1205,w=1856 IOPS][eta 02Jobs: 1 (f=1): [m(1)][58.1%][r=4848KiB/s,w=7399KiB/s][r=1212,w=1849 IOPS][eta 02Jobs: 1 (f=1): [m(1)][58.5%][r=4904KiB/s,w=7343KiB/s][r=1226,w=1835 IOPS][eta 02Jobs: 1 (f=1): [m(1)][58.8%][r=4948KiB/s,w=7292KiB/s][r=1237,w=1823 IOPS][eta 02Jobs: 1 (f=1): [m(1)][59.1%][r=4688KiB/s,w=7559KiB/s][r=1172,w=1889 IOPS][eta 02Jobs: 1 (f=1): [m(1)][59.5%][r=4780KiB/s,w=7467KiB/s][r=1195,w=1866 IOPS][eta 02Jobs: 1 (f=1): [m(1)][59.8%][r=4884KiB/s,w=7368KiB/s][r=1221,w=1842 IOPS][eta 02Jobs: 1 (f=1): [m(1)][60.1%][r=5065KiB/s,w=7183KiB/s][r=1266,w=1795 IOPS][eta 02Jobs: 1 (f=1): [m(1)][60.5%][r=4736KiB/s,w=7419KiB/s][r=1184,w=1854 IOPS][eta 01Jobs: 1 (f=1): [m(1)][60.8%][r=4868KiB/s,w=7215KiB/s][r=1217,w=1803 IOPS][eta 01Jobs: 1 (f=1): [m(1)][61.1%][r=4868KiB/s,w=7448KiB/s][r=1217,w=1862 IOPS][eta 01Jobs: 1 (f=1): [m(1)][61.5%][r=4760KiB/s,w=7623KiB/s][r=1190,w=1905 IOPS][eta 01Jobs: 1 (f=1): [m(1)][61.8%][r=4888KiB/s,w=7411KiB/s][r=1222,w=1852 IOPS][eta 01Jobs: 1 (f=1): [m(1)][62.1%][r=4752KiB/s,w=7400KiB/s][r=1188,w=1850 IOPS][eta 01Jobs: 1 (f=1): [m(1)][62.5%][r=4808KiB/s,w=7475KiB/s][r=1202,w=1868 IOPS][eta 01Jobs: 1 (f=1): [m(1)][62.8%][r=4924KiB/s,w=7371KiB/s][r=1231,w=1842 IOPS][eta 01Jobs: 1 (f=1): [m(1)][63.1%][r=4988KiB/s,w=7239KiB/s][r=1247,w=1809 IOPS][eta 01Jobs: 1 (f=1): [m(1)][63.5%][r=4944KiB/s,w=7252KiB/s][r=1236,w=1813 IOPS][eta 01Jobs: 1 (f=1): [m(1)][63.8%][r=5225KiB/s,w=7103KiB/s][r=1306,w=1775 IOPS][eta 01Jobs: 1 (f=1): [m(1)][64.1%][r=4896KiB/s,w=7359KiB/s][r=1224,w=1839 IOPS][eta 01Jobs: 1 (f=1): [m(1)][64.5%][r=4788KiB/s,w=7415KiB/s][r=1197,w=1853 IOPS][eta 01Jobs: 1 (f=1): [m(1)][64.8%][r=4892KiB/s,w=7388KiB/s][r=1223,w=1847 IOPS][eta 01Jobs: 1 (f=1): [m(1)][65.1%][r=5069KiB/s,w=7159KiB/s][r=1267,w=1789 IOPS][eta 01Jobs: 1 (f=1): [m(1)][65.4%][r=5005KiB/s,w=7143KiB/s][r=1251,w=1785 IOPS][eta 01Jobs: 1 (f=1): [m(1)][65.8%][r=4884KiB/s,w=7420KiB/s][r=1221,w=1855 IOPS][eta 01Jobs: 1 (f=1): [m(1)][66.1%][r=4880KiB/s,w=7319KiB/s][r=1220,w=1829 IOPS][eta 01Jobs: 1 (f=1): [m(1)][66.4%][r=4752KiB/s,w=7491KiB/s][r=1188,w=1872 IOPS][eta 01Jobs: 1 (f=1): [m(1)][66.8%][r=4892KiB/s,w=7379KiB/s][r=1223,w=1844 IOPS][eta 01Jobs: 1 (f=1): [m(1)][67.1%][r=4888KiB/s,w=7420KiB/s][r=1222,w=1855 IOPS][eta 01Jobs: 1 (f=1): [m(1)][67.4%][r=4908KiB/s,w=7395KiB/s][r=1227,w=1848 IOPS][eta 01Jobs: 1 (f=1): [m(1)][67.8%][r=4912KiB/s,w=7335KiB/s][r=1228,w=1833 IOPS][eta 01Jobs: 1 (f=1): [m(1)][68.1%][r=4812KiB/s,w=7267KiB/s][r=1203,w=1816 IOPS][eta 01Jobs: 1 (f=1): [m(1)][68.4%][r=4824KiB/s,w=7591KiB/s][r=1206,w=1897 IOPS][eta 01Jobs: 1 (f=1): [m(1)][68.8%][r=4808KiB/s,w=7436KiB/s][r=1202,w=1859 IOPS][eta 01Jobs: 1 (f=1): [m(1)][69.1%][r=4988KiB/s,w=7259KiB/s][r=1247,w=1814 IOPS][eta 01Jobs: 1 (f=1): [m(1)][69.4%][r=5029KiB/s,w=7219KiB/s][r=1257,w=1804 IOPS][eta 01Jobs: 1 (f=1): [m(1)][69.8%][r=5000KiB/s,w=7248KiB/s][r=1250,w=1812 IOPS][eta 01Jobs: 1 (f=1): [m(1)][70.1%][r=5013KiB/s,w=7235KiB/s][r=1253,w=1808 IOPS][eta 01Jobs: 1 (f=1): [m(1)][70.4%][r=4736KiB/s,w=7319KiB/s][r=1184,w=1829 IOPS][eta 01Jobs: 1 (f=1): [m(1)][70.8%][r=4852KiB/s,w=7583KiB/s][r=1213,w=1895 IOPS][eta 01Jobs: 1 (f=1): [m(1)][71.1%][r=4768KiB/s,w=7484KiB/s][r=1192,w=1871 IOPS][eta 01Jobs: 1 (f=1): [m(1)][71.4%][r=4892KiB/s,w=7359KiB/s][r=1223,w=1839 IOPS][eta 01Jobs: 1 (f=1): [m(1)][71.8%][r=4820KiB/s,w=7419KiB/s][r=1205,w=1854 IOPS][eta 01Jobs: 1 (f=1): [m(1)][72.1%][r=5053KiB/s,w=7199KiB/s][r=1263,w=1799 IOPS][eta 01Jobs: 1 (f=1): [m(1)][72.4%][r=5064KiB/s,w=7188KiB/s][r=1266,w=1797 IOPS][eta 01Jobs: 1 (f=1): [m(1)][72.8%][r=4684KiB/s,w=7307KiB/s][r=1171,w=1826 IOPS][eta 01Jobs: 1 (f=1): [m(1)][73.1%][r=5101KiB/s,w=7403KiB/s][r=1275,w=1850 IOPS][eta 01Jobs: 1 (f=1): [m(1)][73.4%][r=4896KiB/s,w=7351KiB/s][r=1224,w=1837 IOPS][eta 01Jobs: 1 (f=1): [m(1)][73.8%][r=4716KiB/s,w=7532KiB/s][r=1179,w=1883 IOPS][eta 01Jobs: 1 (f=1): [m(1)][74.1%][r=5145KiB/s,w=7107KiB/s][r=1286,w=1776 IOPS][eta 01Jobs: 1 (f=1): [m(1)][74.4%][r=4804KiB/s,w=7191KiB/s][r=1201,w=1797 IOPS][eta 01Jobs: 1 (f=1): [m(1)][74.8%][r=4972KiB/s,w=7527KiB/s][r=1243,w=1881 IOPS][eta 01Jobs: 1 (f=1): [m(1)][75.1%][r=5036KiB/s,w=7060KiB/s][r=1259,w=1765 IOPS][eta 01Jobs: 1 (f=1): [m(1)][75.4%][r=5165KiB/s,w=7235KiB/s][r=1291,w=1808 IOPS][eta 01Jobs: 1 (f=1): [m(1)][75.7%][r=4760KiB/s,w=7395KiB/s][r=1190,w=1848 IOPS][eta 01Jobs: 1 (f=1): [m(1)][76.1%][r=5096KiB/s,w=7168KiB/s][r=1274,w=1792 IOPS][eta 01Jobs: 1 (f=1): [m(1)][76.4%][r=4612KiB/s,w=7603KiB/s][r=1153,w=1900 IOPS][eta 01Jobs: 1 (f=1): [m(1)][76.7%][r=4772KiB/s,w=7559KiB/s][r=1193,w=1889 IOPS][eta 01Jobs: 1 (f=1): [m(1)][77.1%][r=4796KiB/s,w=7331KiB/s][r=1199,w=1832 IOPS][eta 01Jobs: 1 (f=1): [m(1)][77.4%][r=4964KiB/s,w=7396KiB/s][r=1241,w=1849 IOPS][eta 01Jobs: 1 (f=1): [m(1)][77.7%][r=4792KiB/s,w=7479KiB/s][r=1198,w=1869 IOPS][eta 01Jobs: 1 (f=1): [m(1)][78.1%][r=5009KiB/s,w=7179KiB/s][r=1252,w=1794 IOPS][eta 01Jobs: 1 (f=1): [m(1)][78.4%][r=4944KiB/s,w=7351KiB/s][r=1236,w=1837 IOPS][eta 01Jobs: 1 (f=1): [m(1)][78.7%][r=5148KiB/s,w=7048KiB/s][r=1287,w=1762 IOPS][eta 01Jobs: 1 (f=1): [m(1)][79.1%][r=5017KiB/s,w=7175KiB/s][r=1254,w=1793 IOPS][eta 01Jobs: 1 (f=1): [m(1)][79.4%][r=5001KiB/s,w=7291KiB/s][r=1250,w=1822 IOPS][eta 01Jobs: 1 (f=1): [m(1)][79.7%][r=4784KiB/s,w=7395KiB/s][r=1196,w=1848 IOPS][eta 01Jobs: 1 (f=1): [m(1)][80.1%][r=5032KiB/s,w=7272KiB/s][r=1258,w=1818 IOPS][eta 01Jobs: 1 (f=1): [m(1)][80.4%][r=5045KiB/s,w=7243KiB/s][r=1261,w=1810 IOPS][eta 00Jobs: 1 (f=1): [m(1)][80.7%][r=4924KiB/s,w=7347KiB/s][r=1231,w=1836 IOPS][eta 00Jobs: 1 (f=1): [m(1)][81.1%][r=4792KiB/s,w=7492KiB/s][r=1198,w=1873 IOPS][eta 00Jobs: 1 (f=1): [m(1)][81.4%][r=4964KiB/s,w=7287KiB/s][r=1241,w=1821 IOPS][eta 00Jobs: 1 (f=1): [m(1)][81.7%][r=4736KiB/s,w=7287KiB/s][r=1184,w=1821 IOPS][eta 00Jobs: 1 (f=1): [m(1)][82.1%][r=4984KiB/s,w=7384KiB/s][r=1246,w=1846 IOPS][eta 00Jobs: 1 (f=1): [m(1)][82.4%][r=4784KiB/s,w=7567KiB/s][r=1196,w=1891 IOPS][eta 00Jobs: 1 (f=1): [m(1)][82.7%][r=5105KiB/s,w=7143KiB/s][r=1276,w=1785 IOPS][eta 00Jobs: 1 (f=1): [m(1)][83.1%][r=4832KiB/s,w=7415KiB/s][r=1208,w=1853 IOPS][eta 00Jobs: 1 (f=1): [m(1)][83.4%][r=5000KiB/s,w=7252KiB/s][r=1250,w=1813 IOPS][eta 00Jobs: 1 (f=1): [m(1)][83.7%][r=4852KiB/s,w=7391KiB/s][r=1213,w=1847 IOPS][eta 00Jobs: 1 (f=1): [m(1)][84.1%][r=4856KiB/s,w=7391KiB/s][r=1214,w=1847 IOPS][eta 00Jobs: 1 (f=1): [m(1)][84.4%][r=4820KiB/s,w=7431KiB/s][r=1205,w=1857 IOPS][eta 00Jobs: 1 (f=1): [m(1)][84.7%][r=4956KiB/s,w=7244KiB/s][r=1239,w=1811 IOPS][eta 00Jobs: 1 (f=1): [m(1)][85.0%][r=4960KiB/s,w=7335KiB/s][r=1240,w=1833 IOPS][eta 00Jobs: 1 (f=1): [m(1)][85.4%][r=4916KiB/s,w=7331KiB/s][r=1229,w=1832 IOPS][eta 00Jobs: 1 (f=1): [m(1)][85.7%][r=5021KiB/s,w=7227KiB/s][r=1255,w=1806 IOPS][eta 00Jobs: 1 (f=1): [m(1)][86.0%][r=4924KiB/s,w=7328KiB/s][r=1231,w=1832 IOPS][eta 00Jobs: 1 (f=1): [m(1)][86.4%][r=5017KiB/s,w=7231KiB/s][r=1254,w=1807 IOPS][eta 00Jobs: 1 (f=1): [m(1)][86.7%][r=5061KiB/s,w=7187KiB/s][r=1265,w=1796 IOPS][eta 00Jobs: 1 (f=1): [m(1)][87.0%][r=4784KiB/s,w=7312KiB/s][r=1196,w=1828 IOPS][eta 00Jobs: 1 (f=1): [m(1)][87.4%][r=4860KiB/s,w=7543KiB/s][r=1215,w=1885 IOPS][eta 00Jobs: 1 (f=1): [m(1)][87.7%][r=4864KiB/s,w=7379KiB/s][r=1216,w=1844 IOPS][eta 00Jobs: 1 (f=1): [m(1)][88.0%][r=4760KiB/s,w=7491KiB/s][r=1190,w=1872 IOPS][eta 00Jobs: 1 (f=1): [m(1)][88.4%][r=4944KiB/s,w=7300KiB/s][r=1236,w=1825 IOPS][eta 00Jobs: 1 (f=1): [m(1)][88.7%][r=4984KiB/s,w=7259KiB/s][r=1246,w=1814 IOPS][eta 00Jobs: 1 (f=1): [m(1)][89.0%][r=4868KiB/s,w=7379KiB/s][r=1217,w=1844 IOPS][eta 00Jobs: 1 (f=1): [m(1)][89.4%][r=5084KiB/s,w=7164KiB/s][r=1271,w=1791 IOPS][eta 00Jobs: 1 (f=1): [m(1)][89.7%][r=4768KiB/s,w=7479KiB/s][r=1192,w=1869 IOPS][eta 00Jobs: 1 (f=1): [m(1)][90.0%][r=4796KiB/s,w=7451KiB/s][r=1199,w=1862 IOPS][eta 00Jobs: 1 (f=1): [m(1)][90.4%][r=4848KiB/s,w=7299KiB/s][r=1212,w=1824 IOPS][eta 00Jobs: 1 (f=1): [m(1)][90.7%][r=5056KiB/s,w=7204KiB/s][r=1264,w=1801 IOPS][eta 00Jobs: 1 (f=1): [m(1)][91.0%][r=5025KiB/s,w=7307KiB/s][r=1256,w=1826 IOPS][eta 00Jobs: 1 (f=1): [m(1)][91.4%][r=5081KiB/s,w=7171KiB/s][r=1270,w=1792 IOPS][eta 00Jobs: 1 (f=1): [m(1)][91.7%][r=4700KiB/s,w=7551KiB/s][r=1175,w=1887 IOPS][eta 00Jobs: 1 (f=1): [m(1)][92.0%][r=4840KiB/s,w=7408KiB/s][r=1210,w=1852 IOPS][eta 00Jobs: 1 (f=1): [m(1)][92.4%][r=4868KiB/s,w=7383KiB/s][r=1217,w=1845 IOPS][eta 00Jobs: 1 (f=1): [m(1)][92.7%][r=4836KiB/s,w=7411KiB/s][r=1209,w=1852 IOPS][eta 00Jobs: 1 (f=1): [m(1)][93.0%][r=4812KiB/s,w=7435KiB/s][r=1203,w=1858 IOPS][eta 00Jobs: 1 (f=1): [m(1)][93.4%][r=4972KiB/s,w=7280KiB/s][r=1243,w=1820 IOPS][eta 00Jobs: 1 (f=1): [m(1)][93.7%][r=4976KiB/s,w=7143KiB/s][r=1244,w=1785 IOPS][eta 00Jobs: 1 (f=1): [m(1)][94.0%][r=4832KiB/s,w=7443KiB/s][r=1208,w=1860 IOPS][eta 00Jobs: 1 (f=1): [m(1)][94.4%][r=5020KiB/s,w=7244KiB/s][r=1255,w=1811 IOPS][eta 00Jobs: 1 (f=1): [m(1)][94.7%][r=4936KiB/s,w=7327KiB/s][r=1234,w=1831 IOPS][eta 00Jobs: 1 (f=1): [m(1)][95.0%][r=4736KiB/s,w=7579KiB/s][r=1184,w=1894 IOPS][eta 00Jobs: 1 (f=1): [m(1)][95.3%][r=4968KiB/s,w=7279KiB/s][r=1242,w=1819 IOPS][eta 00Jobs: 1 (f=1): [m(1)][95.7%][r=4908KiB/s,w=7344KiB/s][r=1227,w=1836 IOPS][eta 00Jobs: 1 (f=1): [m(1)][96.0%][r=4940KiB/s,w=7307KiB/s][r=1235,w=1826 IOPS][eta 00Jobs: 1 (f=1): [m(1)][96.3%][r=4692KiB/s,w=7555KiB/s][r=1173,w=1888 IOPS][eta 00Jobs: 1 (f=1): [m(1)][96.7%][r=4944KiB/s,w=7303KiB/s][r=1236,w=1825 IOPS][eta 00Jobs: 1 (f=1): [m(1)][97.0%][r=4708KiB/s,w=7544KiB/s][r=1177,w=1886 IOPS][eta 00Jobs: 1 (f=1): [m(1)][97.3%][r=4904KiB/s,w=7343KiB/s][r=1226,w=1835 IOPS][eta 00Jobs: 1 (f=1): [m(1)][97.7%][r=4852KiB/s,w=7279KiB/s][r=1213,w=1819 IOPS][eta 00Jobs: 1 (f=1): [m(1)][98.0%][r=4928KiB/s,w=7351KiB/s][r=1232,w=1837 IOPS][eta 00Jobs: 1 (f=1): [m(1)][98.3%][r=5080KiB/s,w=7228KiB/s][r=1270,w=1807 IOPS][eta 00Jobs: 1 (f=1): [m(1)][98.7%][r=4820KiB/s,w=7447KiB/s][r=1205,w=1861 IOPS][eta 00Jobs: 1 (f=1): [m(1)][99.0%][r=5145KiB/s,w=7103KiB/s][r=1286,w=1775 IOPS][eta 00Jobs: 1 (f=1): [m(1)][99.3%][r=4968KiB/s,w=7279KiB/s][r=1242,w=1819 IOPS][eta 00Jobs: 1 (f=1): [m(1)][99.7%][r=4968KiB/s,w=7284KiB/s][r=1242,w=1821 IOPS][eta 00Jobs: 1 (f=1): [m(1)][100.0%][r=4780KiB/s,w=7467KiB/s][r=1195,w=1866 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=27749: Sun Oct  8 09:06:33 2017
   read: IOPS=1229, BW=4917KiB/s (5035kB/s)(1440MiB/300002msec)
    slat (nsec): min=1464, max=1495.2k, avg=6098.37, stdev=4963.75
    clat (usec): min=10, max=21637, avg=966.63, stdev=597.06
     lat (usec): min=153, max=21645, avg=972.95, stdev=597.27
    clat percentiles (usec):
     |  1.00th=[  194],  5.00th=[  237], 10.00th=[  334], 20.00th=[  404],
     | 30.00th=[  494], 40.00th=[  996], 50.00th=[ 1106], 60.00th=[ 1188],
     | 70.00th=[ 1237], 80.00th=[ 1287], 90.00th=[ 1352], 95.00th=[ 1483],
     | 99.00th=[ 2966], 99.50th=[ 3884], 99.90th=[ 6063], 99.95th=[ 7504],
     | 99.99th=[12780]
   bw (  KiB/s): min= 4152, max=11824, per=100.00%, avg=4916.01, stdev=348.98, samples=600
   iops        : min= 1038, max= 2956, avg=1228.98, stdev=87.25, samples=600
  write: IOPS=1840, BW=7363KiB/s (7540kB/s)(2157MiB/300002msec)
    slat (nsec): min=1706, max=1425.3k, avg=6534.34, stdev=3506.62
    clat (usec): min=337, max=32382, avg=1514.15, stdev=2342.19
     lat (usec): min=343, max=32387, avg=1520.90, stdev=2342.34
    clat percentiles (usec):
     |  1.00th=[  416],  5.00th=[  453], 10.00th=[  482], 20.00th=[  537],
     | 30.00th=[  709], 40.00th=[ 1205], 50.00th=[ 1270], 60.00th=[ 1319],
     | 70.00th=[ 1352], 80.00th=[ 1401], 90.00th=[ 1532], 95.00th=[ 1680],
     | 99.00th=[13829], 99.50th=[14746], 99.90th=[20317], 99.95th=[22414],
     | 99.99th=[26084]
   bw (  KiB/s): min= 6184, max=17584, per=99.99%, avg=7362.43, stdev=497.17, samples=600
   iops        : min= 1546, max= 4396, avg=1840.60, stdev=124.29, samples=600
  lat (usec)   : 20=0.01%, 100=0.01%, 250=2.42%, 500=17.86%, 750=12.11%
  lat (usec)   : 1000=4.84%
  lat (msec)   : 2=59.39%, 4=0.86%, 10=0.47%, 20=1.97%, 50=0.07%
  cpu          : usr=0.99%, sys=3.03%, ctx=865034, majf=0, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=368744,552248,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=4917KiB/s (5035kB/s), 4917KiB/s-4917KiB/s (5035kB/s-5035kB/s), io=1440MiB (1510MB), run=300002-300002msec
  WRITE: bw=7363KiB/s (7540kB/s), 7363KiB/s-7363KiB/s (7540kB/s-7540kB/s), io=2157MiB (2262MB), run=300002-300002msec

Disk stats (read/write):
  xvda: ios=368670/552099, merge=0/14, ticks=358864/836836, in_queue=1195688, util=100.00%
```

*file-size*
```
ls -al test4K-rw-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  8 09:06 test4K-rw-aio
```

## gcloud micro - 585M
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            286M     0  286M   0% /dev
tmpfs            59M  6.5M   53M  11% /run
/dev/sda1        30G  2.4G   27G   9% /
tmpfs           294M     0  294M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           294M     0  294M   0% /sys/fs/cgroup
tmpfs            59M     0   59M   0% /run/user/901
```

*rw*
```
./fio --filename=test4K-rw-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randrw --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G --rwmixread=40
myjob: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [m(1)][1.0%][r=940KiB/s,w=1416KiB/s][r=235,w=354 IOPS][eta 04m:58Jobs: 1 (f=1): [m(1)][1.3%][r=952KiB/s,w=1329KiB/s][r=238,w=332 IOPS][eta 04m:57Jobs: 1 (f=1): [m(1)][1.7%][r=960KiB/s,w=1316KiB/s][r=240,w=329 IOPS][eta 04m:56Jobs: 1 (f=1): [m(1)][2.0%][r=988KiB/s,w=1541KiB/s][r=247,w=385 IOPS][eta 04m:55Jobs: 1 (f=1): [m(1)][2.3%][r=960KiB/s,w=1436KiB/s][r=240,w=359 IOPS][eta 04m:54Jobs: 1 (f=1): [m(1)][2.7%][r=912KiB/s,w=1353KiB/s][r=228,w=338 IOPS][eta 04m:53Jobs: 1 (f=1): [m(1)][3.0%][r=992KiB/s,w=1452KiB/s][r=248,w=363 IOPS][eta 04m:52Jobs: 1 (f=1): [m(1)][3.3%][r=984KiB/s,w=1545KiB/s][r=246,w=386 IOPS][eta 04m:51Jobs: 1 (f=1): [m(1)][3.7%][r=924KiB/s,w=1409KiB/s][r=231,w=352 IOPS][eta 04m:50Jobs: 1 (f=1): [m(1)][4.0%][r=912KiB/s,w=1340KiB/s][r=228,w=335 IOPS][eta 04m:49Jobs: 1 (f=1): [m(1)][4.3%][r=924KiB/s,w=1617KiB/s][r=231,w=404 IOPS][eta 04m:48Jobs: 1 (f=1): [m(1)][4.7%][r=872KiB/s,w=1260KiB/s][r=218,w=315 IOPS][eta 04m:47Jobs: 1 (f=1): [m(1)][5.0%][r=884KiB/s,w=1225KiB/s][r=221,w=306 IOPS][eta 04m:46Jobs: 1 (f=1): [m(1)][5.3%][r=884KiB/s,w=1220KiB/s][r=221,w=305 IOPS][eta 04m:45Jobs: 1 (f=1): [m(1)][5.6%][r=924KiB/s,w=1473KiB/s][r=231,w=368 IOPS][eta 04m:44Jobs: 1 (f=1): [m(1)][6.0%][r=928KiB/s,w=1436KiB/s][r=232,w=359 IOPS][eta 04m:43Jobs: 1 (f=1): [m(1)][6.3%][r=892KiB/s,w=1381KiB/s][r=223,w=345 IOPS][eta 04m:42Jobs: 1 (f=1): [m(1)][6.6%][r=896KiB/s,w=1420KiB/s][r=224,w=355 IOPS][eta 04m:41Jobs: 1 (f=1): [m(1)][7.0%][r=844KiB/s,w=1205KiB/s][r=211,w=301 IOPS][eta 04m:40Jobs: 1 (f=1): [m(1)][7.3%][r=912KiB/s,w=1540KiB/s][r=228,w=385 IOPS][eta 04m:39Jobs: 1 (f=1): [m(1)][7.6%][r=920KiB/s,w=1193KiB/s][r=230,w=298 IOPS][eta 04m:38Jobs: 1 (f=1): [m(1)][8.0%][r=944KiB/s,w=1264KiB/s][r=236,w=316 IOPS][eta 04m:37Jobs: 1 (f=1): [m(1)][8.3%][r=848KiB/s,w=1437KiB/s][r=212,w=359 IOPS][eta 04m:36Jobs: 1 (f=1): [m(1)][8.6%][r=876KiB/s,w=1424KiB/s][r=219,w=356 IOPS][eta 04m:35Jobs: 1 (f=1): [m(1)][9.0%][r=880KiB/s,w=1345KiB/s][r=220,w=336 IOPS][eta 04m:34Jobs: 1 (f=1): [m(1)][9.3%][r=900KiB/s,w=1289KiB/s][r=225,w=322 IOPS][eta 04m:33Jobs: 1 (f=1): [m(1)][9.6%][r=872KiB/s,w=1260KiB/s][r=218,w=315 IOPS][eta 04m:32Jobs: 1 (f=1): [m(1)][10.0%][r=896KiB/s,w=1237KiB/s][r=224,w=309 IOPS][eta 04m:3Jobs: 1 (f=1): [m(1)][10.3%][r=876KiB/s,w=1408KiB/s][r=219,w=352 IOPS][eta 04m:3Jobs: 1 (f=1): [m(1)][10.6%][r=932KiB/s,w=1377KiB/s][r=233,w=344 IOPS][eta 04m:2Jobs: 1 (f=1): [m(1)][11.0%][r=880KiB/s,w=1348KiB/s][r=220,w=337 IOPS][eta 04m:2Jobs: 1 (f=1): [m(1)][11.3%][r=892KiB/s,w=1457KiB/s][r=223,w=364 IOPS][eta 04m:2Jobs: 1 (f=1): [m(1)][11.6%][r=876KiB/s,w=1260KiB/s][r=219,w=315 IOPS][eta 04m:2Jobs: 1 (f=1): [m(1)][12.0%][r=868KiB/s,w=1441KiB/s][r=217,w=360 IOPS][eta 04m:2Jobs: 1 (f=1): [m(1)][12.3%][r=832KiB/s,w=1281KiB/s][r=208,w=320 IOPS][eta 04m:2Jobs: 1 (f=1): [m(1)][12.6%][r=828KiB/s,w=1300KiB/s][r=207,w=325 IOPS][eta 04m:2Jobs: 1 (f=1): [m(1)][13.0%][r=840KiB/s,w=1421KiB/s][r=210,w=355 IOPS][eta 04m:2Jobs: 1 (f=1): [m(1)][13.3%][r=900KiB/s,w=1280KiB/s][r=225,w=320 IOPS][eta 04m:2Jobs: 1 (f=1): [m(1)][13.6%][r=888KiB/s,w=1317KiB/s][r=222,w=329 IOPS][eta 04m:2Jobs: 1 (f=1): [m(1)][14.0%][r=880KiB/s,w=1216KiB/s][r=220,w=304 IOPS][eta 04m:1Jobs: 1 (f=1): [m(1)][14.3%][r=996KiB/s,w=1729KiB/s][r=249,w=432 IOPS][eta 04m:1Jobs: 1 (f=1): [m(1)][14.6%][r=952KiB/s,w=1296KiB/s][r=238,w=324 IOPS][eta 04m:1Jobs: 1 (f=1): [m(1)][15.0%][r=968KiB/s,w=1569KiB/s][r=242,w=392 IOPS][eta 04m:1Jobs: 1 (f=1): [m(1)][15.3%][r=916KiB/s,w=1108KiB/s][r=229,w=277 IOPS][eta 04m:1Jobs: 1 (f=1): [m(1)][15.6%][r=916KiB/s,w=1649KiB/s][r=229,w=412 IOPS][eta 04m:1Jobs: 1 (f=1): [m(1)][15.9%][r=944KiB/s,w=1412KiB/s][r=236,w=353 IOPS][eta 04m:1Jobs: 1 (f=1): [m(1)][16.3%][r=880KiB/s,w=1349KiB/s][r=220,w=337 IOPS][eta 04m:1Jobs: 1 (f=1): [m(1)][16.6%][r=928KiB/s,w=1464KiB/s][r=232,w=366 IOPS][eta 04m:1Jobs: 1 (f=1): [m(1)][16.9%][r=924KiB/s,w=1153KiB/s][r=231,w=288 IOPS][eta 04m:1Jobs: 1 (f=1): [m(1)][17.3%][r=924KiB/s,w=1436KiB/s][r=231,w=359 IOPS][eta 04m:0Jobs: 1 (f=1): [m(1)][17.6%][r=864KiB/s,w=1401KiB/s][r=216,w=350 IOPS][eta 04m:0Jobs: 1 (f=1): [m(1)][17.9%][r=900KiB/s,w=1460KiB/s][r=225,w=365 IOPS][eta 04m:0Jobs: 1 (f=1): [m(1)][18.3%][r=900KiB/s,w=1337KiB/s][r=225,w=334 IOPS][eta 04m:0Jobs: 1 (f=1): [m(1)][18.6%][r=904KiB/s,w=1285KiB/s][r=226,w=321 IOPS][eta 04m:0Jobs: 1 (f=1): [m(1)][18.9%][r=900KiB/s,w=1388KiB/s][r=225,w=347 IOPS][eta 04m:0Jobs: 1 (f=1): [m(1)][19.3%][r=924KiB/s,w=1541KiB/s][r=231,w=385 IOPS][eta 04m:0Jobs: 1 (f=1): [m(1)][19.6%][r=928KiB/s,w=1180KiB/s][r=232,w=295 IOPS][eta 04m:0Jobs: 1 (f=1): [m(1)][19.9%][r=872KiB/s,w=1521KiB/s][r=218,w=380 IOPS][eta 04m:0Jobs: 1 (f=1): [m(1)][20.3%][r=932KiB/s,w=1372KiB/s][r=233,w=343 IOPS][eta 04m:0Jobs: 1 (f=1): [m(1)][20.6%][r=856KiB/s,w=1293KiB/s][r=214,w=323 IOPS][eta 03m:5Jobs: 1 (f=1): [m(1)][20.9%][r=884KiB/s,w=1540KiB/s][r=221,w=385 IOPS][eta 03m:5Jobs: 1 (f=1): [m(1)][21.3%][r=960KiB/s,w=1357KiB/s][r=240,w=339 IOPS][eta 03m:5Jobs: 1 (f=1): [m(1)][21.6%][r=940KiB/s,w=1416KiB/s][r=235,w=354 IOPS][eta 03m:5Jobs: 1 (f=1): [m(1)][21.9%][r=856KiB/s,w=1253KiB/s][r=214,w=313 IOPS][eta 03m:5Jobs: 1 (f=1): [m(1)][22.3%][r=916KiB/s,w=1332KiB/s][r=229,w=333 IOPS][eta 03m:5Jobs: 1 (f=1): [m(1)][22.6%][r=920KiB/s,w=1309KiB/s][r=230,w=327 IOPS][eta 03m:5Jobs: 1 (f=1): [m(1)][22.9%][r=960KiB/s,w=1520KiB/s][r=240,w=380 IOPS][eta 03m:5Jobs: 1 (f=1): [m(1)][23.3%][r=892KiB/s,w=1285KiB/s][r=223,w=321 IOPS][eta 03m:5Jobs: 1 (f=1): [m(1)][23.6%][r=916KiB/s,w=1376KiB/s][r=229,w=344 IOPS][eta 03m:5Jobs: 1 (f=1): [m(1)][23.9%][r=892KiB/s,w=1253KiB/s][r=223,w=313 IOPS][eta 03m:4Jobs: 1 (f=1): [m(1)][24.3%][r=924KiB/s,w=1384KiB/s][r=231,w=346 IOPS][eta 03m:4Jobs: 1 (f=1): [m(1)][24.6%][r=892KiB/s,w=1469KiB/s][r=223,w=367 IOPS][eta 03m:4Jobs: 1 (f=1): [m(1)][24.9%][r=940KiB/s,w=1492KiB/s][r=235,w=373 IOPS][eta 03m:4Jobs: 1 (f=1): [m(1)][25.2%][r=936KiB/s,w=1481KiB/s][r=234,w=370 IOPS][eta 03m:4Jobs: 1 (f=1): [m(1)][25.6%][r=876KiB/s,w=1420KiB/s][r=219,w=355 IOPS][eta 03m:4Jobs: 1 (f=1): [m(1)][25.9%][r=920KiB/s,w=1281KiB/s][r=230,w=320 IOPS][eta 03m:4Jobs: 1 (f=1): [m(1)][26.2%][r=932KiB/s,w=1244KiB/s][r=233,w=311 IOPS][eta 03m:4Jobs: 1 (f=1): [m(1)][26.6%][r=924KiB/s,w=1517KiB/s][r=231,w=379 IOPS][eta 03m:4Jobs: 1 (f=1): [m(1)][26.9%][r=932KiB/s,w=1260KiB/s][r=233,w=315 IOPS][eta 03m:4Jobs: 1 (f=1): [m(1)][27.2%][r=880KiB/s,w=1369KiB/s][r=220,w=342 IOPS][eta 03m:3Jobs: 1 (f=1): [m(1)][27.6%][r=996KiB/s,w=1268KiB/s][r=249,w=317 IOPS][eta 03m:3Jobs: 1 (f=1): [m(1)][27.9%][r=924KiB/s,w=1349KiB/s][r=231,w=337 IOPS][eta 03m:3Jobs: 1 (f=1): [m(1)][28.2%][r=932KiB/s,w=1229KiB/s][r=233,w=307 IOPS][eta 03m:3Jobs: 1 (f=1): [m(1)][28.6%][r=828KiB/s,w=1476KiB/s][r=207,w=369 IOPS][eta 03m:3Jobs: 1 (f=1): [m(1)][28.9%][r=912KiB/s,w=1389KiB/s][r=228,w=347 IOPS][eta 03m:3Jobs: 1 (f=1): [m(1)][29.2%][r=900KiB/s,w=1292KiB/s][r=225,w=323 IOPS][eta 03m:3Jobs: 1 (f=1): [m(1)][29.6%][r=904KiB/s,w=1297KiB/s][r=226,w=324 IOPS][eta 03m:3Jobs: 1 (f=1): [m(1)][29.9%][r=940KiB/s,w=1248KiB/s][r=235,w=312 IOPS][eta 03m:3Jobs: 1 (f=1): [m(1)][30.2%][r=924KiB/s,w=1325KiB/s][r=231,w=331 IOPS][eta 03m:3Jobs: 1 (f=1): [m(1)][30.6%][r=872KiB/s,w=1416KiB/s][r=218,w=354 IOPS][eta 03m:2Jobs: 1 (f=1): [m(1)][30.9%][r=912KiB/s,w=1317KiB/s][r=228,w=329 IOPS][eta 03m:2Jobs: 1 (f=1): [m(1)][31.2%][r=956KiB/s,w=1460KiB/s][r=239,w=365 IOPS][eta 03m:2Jobs: 1 (f=1): [m(1)][31.6%][r=876KiB/s,w=1437KiB/s][r=219,w=359 IOPS][eta 03m:2Jobs: 1 (f=1): [m(1)][31.9%][r=900KiB/s,w=1372KiB/s][r=225,w=343 IOPS][eta 03m:2Jobs: 1 (f=1): [m(1)][32.2%][r=904KiB/s,w=1229KiB/s][r=226,w=307 IOPS][eta 03m:2Jobs: 1 (f=1): [m(1)][32.6%][r=904KiB/s,w=1224KiB/s][r=226,w=306 IOPS][eta 03m:2Jobs: 1 (f=1): [m(1)][32.9%][r=912KiB/s,w=1433KiB/s][r=228,w=358 IOPS][eta 03m:2Jobs: 1 (f=1): [m(1)][33.2%][r=896KiB/s,w=1628KiB/s][r=224,w=407 IOPS][eta 03m:2Jobs: 1 (f=1): [m(1)][33.6%][r=968KiB/s,w=1721KiB/s][r=242,w=430 IOPS][eta 03m:2Jobs: 1 (f=1): [m(1)][33.9%][r=904KiB/s,w=1452KiB/s][r=226,w=363 IOPS][eta 03m:1Jobs: 1 (f=1): [m(1)][34.2%][r=888KiB/s,w=1185KiB/s][r=222,w=296 IOPS][eta 03m:1Jobs: 1 (f=1): [m(1)][34.6%][r=1004KiB/s,w=1384KiB/s][r=251,w=346 IOPS][eta 03m:Jobs: 1 (f=1): [m(1)][34.9%][r=856KiB/s,w=1213KiB/s][r=214,w=303 IOPS][eta 03m:1Jobs: 1 (f=1): [m(1)][35.2%][r=928KiB/s,w=1504KiB/s][r=232,w=376 IOPS][eta 03m:1Jobs: 1 (f=1): [m(1)][35.5%][r=940KiB/s,w=1253KiB/s][r=235,w=313 IOPS][eta 03m:1Jobs: 1 (f=1): [m(1)][35.9%][r=824KiB/s,w=1380KiB/s][r=206,w=345 IOPS][eta 03m:1Jobs: 1 (f=1): [m(1)][36.2%][r=884KiB/s,w=1153KiB/s][r=221,w=288 IOPS][eta 03m:1Jobs: 1 (f=1): [m(1)][36.5%][r=876KiB/s,w=1392KiB/s][r=219,w=348 IOPS][eta 03m:1Jobs: 1 (f=1): [m(1)][36.9%][r=888KiB/s,w=1241KiB/s][r=222,w=310 IOPS][eta 03m:1Jobs: 1 (f=1): [m(1)][37.2%][r=880KiB/s,w=1424KiB/s][r=220,w=356 IOPS][eta 03m:0Jobs: 1 (f=1): [m(1)][37.5%][r=924KiB/s,w=1337KiB/s][r=231,w=334 IOPS][eta 03m:0Jobs: 1 (f=1): [m(1)][37.9%][r=924KiB/s,w=1289KiB/s][r=231,w=322 IOPS][eta 03m:0Jobs: 1 (f=1): [m(1)][38.2%][r=904KiB/s,w=1556KiB/s][r=226,w=389 IOPS][eta 03m:0Jobs: 1 (f=1): [m(1)][38.5%][r=936KiB/s,w=1465KiB/s][r=234,w=366 IOPS][eta 03m:0Jobs: 1 (f=1): [m(1)][38.9%][r=852KiB/s,w=1236KiB/s][r=213,w=309 IOPS][eta 03m:0Jobs: 1 (f=1): [m(1)][39.2%][r=960KiB/s,w=1233KiB/s][r=240,w=308 IOPS][eta 03m:0Jobs: 1 (f=1): [m(1)][39.5%][r=952KiB/s,w=1420KiB/s][r=238,w=355 IOPS][eta 03m:0Jobs: 1 (f=1): [m(1)][39.9%][r=952KiB/s,w=1404KiB/s][r=238,w=351 IOPS][eta 03m:0Jobs: 1 (f=1): [m(1)][40.2%][r=964KiB/s,w=1353KiB/s][r=241,w=338 IOPS][eta 03m:0Jobs: 1 (f=1): [m(1)][40.5%][r=844KiB/s,w=1248KiB/s][r=211,w=312 IOPS][eta 02m:5Jobs: 1 (f=1): [m(1)][40.9%][r=872KiB/s,w=1333KiB/s][r=218,w=333 IOPS][eta 02m:5Jobs: 1 (f=1): [m(1)][41.2%][r=984KiB/s,w=1497KiB/s][r=246,w=374 IOPS][eta 02m:5Jobs: 1 (f=1): [m(1)][41.5%][r=916KiB/s,w=1400KiB/s][r=229,w=350 IOPS][eta 02m:5Jobs: 1 (f=1): [m(1)][41.9%][r=876KiB/s,w=1409KiB/s][r=219,w=352 IOPS][eta 02m:5Jobs: 1 (f=1): [m(1)][42.2%][r=852KiB/s,w=1220KiB/s][r=213,w=305 IOPS][eta 02m:5Jobs: 1 (f=1): [m(1)][42.5%][r=888KiB/s,w=1337KiB/s][r=222,w=334 IOPS][eta 02m:5Jobs: 1 (f=1): [m(1)][42.9%][r=948KiB/s,w=1552KiB/s][r=237,w=388 IOPS][eta 02m:5Jobs: 1 (f=1): [m(1)][43.2%][r=872KiB/s,w=1369KiB/s][r=218,w=342 IOPS][eta 02m:5Jobs: 1 (f=1): [m(1)][43.5%][r=896KiB/s,w=1220KiB/s][r=224,w=305 IOPS][eta 02m:5Jobs: 1 (f=1): [m(1)][43.9%][r=940KiB/s,w=1353KiB/s][r=235,w=338 IOPS][eta 02m:4Jobs: 1 (f=1): [m(1)][44.2%][r=940KiB/s,w=1348KiB/s][r=235,w=337 IOPS][eta 02m:4Jobs: 1 (f=1): [m(1)][44.5%][r=904KiB/s,w=1577KiB/s][r=226,w=394 IOPS][eta 02m:4Jobs: 1 (f=1): [m(1)][44.9%][r=996KiB/s,w=1497KiB/s][r=249,w=374 IOPS][eta 02m:4Jobs: 1 (f=1): [m(1)][45.2%][r=908KiB/s,w=1444KiB/s][r=227,w=361 IOPS][eta 02m:4Jobs: 1 (f=1): [m(1)][45.5%][r=852KiB/s,w=1453KiB/s][r=213,w=363 IOPS][eta 02m:4Jobs: 1 (f=1): [m(1)][45.8%][r=944KiB/s,w=1364KiB/s][r=236,w=341 IOPS][eta 02m:4Jobs: 1 (f=1): [m(1)][46.2%][r=952KiB/s,w=1537KiB/s][r=238,w=384 IOPS][eta 02m:4Jobs: 1 (f=1): [m(1)][46.5%][r=952KiB/s,w=1528KiB/s][r=238,w=382 IOPS][eta 02m:4Jobs: 1 (f=1): [m(1)][46.8%][r=936KiB/s,w=1301KiB/s][r=234,w=325 IOPS][eta 02m:4Jobs: 1 (f=1): [m(1)][47.2%][r=864KiB/s,w=1588KiB/s][r=216,w=397 IOPS][eta 02m:3Jobs: 1 (f=1): [m(1)][47.5%][r=896KiB/s,w=1169KiB/s][r=224,w=292 IOPS][eta 02m:3Jobs: 1 (f=1): [m(1)][47.8%][r=960KiB/s,w=1580KiB/s][r=240,w=395 IOPS][eta 02m:3Jobs: 1 (f=1): [m(1)][48.2%][r=892KiB/s,w=1137KiB/s][r=223,w=284 IOPS][eta 02m:3Jobs: 1 (f=1): [m(1)][48.5%][r=920KiB/s,w=1312KiB/s][r=230,w=328 IOPS][eta 02m:3Jobs: 1 (f=1): [m(1)][48.8%][r=952KiB/s,w=1612KiB/s][r=238,w=403 IOPS][eta 02m:3Jobs: 1 (f=1): [m(1)][49.2%][r=924KiB/s,w=1429KiB/s][r=231,w=357 IOPS][eta 02m:3Jobs: 1 (f=1): [m(1)][49.5%][r=952KiB/s,w=1320KiB/s][r=238,w=330 IOPS][eta 02m:3Jobs: 1 (f=1): [m(1)][49.8%][r=908KiB/s,w=1317KiB/s][r=227,w=329 IOPS][eta 02m:3Jobs: 1 (f=1): [m(1)][50.2%][r=952KiB/s,w=1353KiB/s][r=238,w=338 IOPS][eta 02m:3Jobs: 1 (f=1): [m(1)][50.5%][r=896KiB/s,w=1452KiB/s][r=224,w=363 IOPS][eta 02m:2Jobs: 1 (f=1): [m(1)][50.8%][r=944KiB/s,w=1457KiB/s][r=236,w=364 IOPS][eta 02m:2Jobs: 1 (f=1): [m(1)][51.2%][r=920KiB/s,w=1172KiB/s][r=230,w=293 IOPS][eta 02m:2Jobs: 1 (f=1): [m(1)][51.5%][r=992KiB/s,w=1413KiB/s][r=248,w=353 IOPS][eta 02m:2Jobs: 1 (f=1): [m(1)][51.8%][r=948KiB/s,w=1333KiB/s][r=237,w=333 IOPS][eta 02m:2Jobs: 1 (f=1): [m(1)][52.2%][r=884KiB/s,w=1372KiB/s][r=221,w=343 IOPS][eta 02m:2Jobs: 1 (f=1): [m(1)][52.5%][r=944KiB/s,w=1349KiB/s][r=236,w=337 IOPS][eta 02m:2Jobs: 1 (f=1): [m(1)][52.8%][r=992KiB/s,w=1464KiB/s][r=248,w=366 IOPS][eta 02m:2Jobs: 1 (f=1): [m(1)][53.2%][r=884KiB/s,w=1261KiB/s][r=221,w=315 IOPS][eta 02m:2Jobs: 1 (f=1): [m(1)][53.5%][r=900KiB/s,w=1276KiB/s][r=225,w=319 IOPS][eta 02m:2Jobs: 1 (f=1): [m(1)][53.8%][r=892KiB/s,w=1229KiB/s][r=223,w=307 IOPS][eta 02m:1Jobs: 1 (f=1): [m(1)][54.2%][r=948KiB/s,w=1424KiB/s][r=237,w=356 IOPS][eta 02m:1Jobs: 1 (f=1): [m(1)][54.5%][r=888KiB/s,w=1437KiB/s][r=222,w=359 IOPS][eta 02m:1Jobs: 1 (f=1): [m(1)][54.8%][r=948KiB/s,w=1432KiB/s][r=237,w=358 IOPS][eta 02m:1Jobs: 1 (f=1): [m(1)][55.1%][r=896KiB/s,w=1497KiB/s][r=224,w=374 IOPS][eta 02m:1Jobs: 1 (f=1): [m(1)][55.5%][r=880KiB/s,w=1392KiB/s][r=220,w=348 IOPS][eta 02m:1Jobs: 1 (f=1): [m(1)][55.8%][r=964KiB/s,w=1097KiB/s][r=241,w=274 IOPS][eta 02m:1Jobs: 1 (f=1): [m(1)][56.1%][r=976KiB/s,w=1373KiB/s][r=244,w=343 IOPS][eta 02m:1Jobs: 1 (f=1): [m(1)][56.5%][r=932KiB/s,w=1336KiB/s][r=233,w=334 IOPS][eta 02m:1Jobs: 1 (f=1): [m(1)][56.8%][r=932KiB/s,w=1521KiB/s][r=233,w=380 IOPS][eta 02m:1Jobs: 1 (f=1): [m(1)][57.1%][r=944KiB/s,w=1272KiB/s][r=236,w=318 IOPS][eta 02m:0Jobs: 1 (f=1): [m(1)][57.5%][r=860KiB/s,w=1341KiB/s][r=215,w=335 IOPS][eta 02m:0Jobs: 1 (f=1): [m(1)][57.8%][r=936KiB/s,w=1720KiB/s][r=234,w=430 IOPS][eta 02m:0Jobs: 1 (f=1): [m(1)][58.1%][r=976KiB/s,w=1389KiB/s][r=244,w=347 IOPS][eta 02m:0Jobs: 1 (f=1): [m(1)][58.5%][r=948KiB/s,w=1468KiB/s][r=237,w=367 IOPS][eta 02m:0Jobs: 1 (f=1): [m(1)][58.8%][r=908KiB/s,w=1313KiB/s][r=227,w=328 IOPS][eta 02m:0Jobs: 1 (f=1): [m(1)][59.1%][r=936KiB/s,w=1344KiB/s][r=234,w=336 IOPS][eta 02m:0Jobs: 1 (f=1): [m(1)][59.5%][r=920KiB/s,w=1493KiB/s][r=230,w=373 IOPS][eta 02m:0Jobs: 1 (f=1): [m(1)][59.8%][r=908KiB/s,w=1380KiB/s][r=227,w=345 IOPS][eta 02m:0Jobs: 1 (f=1): [m(1)][60.1%][r=924KiB/s,w=1213KiB/s][r=231,w=303 IOPS][eta 02m:0Jobs: 1 (f=1): [m(1)][60.5%][r=952KiB/s,w=1184KiB/s][r=238,w=296 IOPS][eta 01m:5Jobs: 1 (f=1): [m(1)][60.8%][r=932KiB/s,w=1349KiB/s][r=233,w=337 IOPS][eta 01m:5Jobs: 1 (f=1): [m(1)][61.1%][r=888KiB/s,w=1172KiB/s][r=222,w=293 IOPS][eta 01m:5Jobs: 1 (f=1): [m(1)][61.5%][r=920KiB/s,w=1221KiB/s][r=230,w=305 IOPS][eta 01m:5Jobs: 1 (f=1): [m(1)][61.8%][r=888KiB/s,w=1348KiB/s][r=222,w=337 IOPS][eta 01m:5Jobs: 1 (f=1): [m(1)][62.1%][r=876KiB/s,w=1421KiB/s][r=219,w=355 IOPS][eta 01m:5Jobs: 1 (f=1): [m(1)][62.5%][r=864KiB/s,w=1244KiB/s][r=216,w=311 IOPS][eta 01m:5Jobs: 1 (f=1): [m(1)][62.8%][r=884KiB/s,w=1433KiB/s][r=221,w=358 IOPS][eta 01m:5Jobs: 1 (f=1): [m(1)][63.1%][r=900KiB/s,w=1237KiB/s][r=225,w=309 IOPS][eta 01m:5Jobs: 1 (f=1): [m(1)][63.5%][r=908KiB/s,w=1652KiB/s][r=227,w=413 IOPS][eta 01m:5Jobs: 1 (f=1): [m(1)][63.8%][r=876KiB/s,w=1213KiB/s][r=219,w=303 IOPS][eta 01m:4Jobs: 1 (f=1): [m(1)][64.1%][r=884KiB/s,w=1208KiB/s][r=221,w=302 IOPS][eta 01m:4Jobs: 1 (f=1): [m(1)][64.5%][r=844KiB/s,w=1144KiB/s][r=211,w=286 IOPS][eta 01m:4Jobs: 1 (f=1): [m(1)][64.8%][r=908KiB/s,w=1329KiB/s][r=227,w=332 IOPS][eta 01m:4Jobs: 1 (f=1): [m(1)][65.1%][r=880KiB/s,w=1241KiB/s][r=220,w=310 IOPS][eta 01m:4Jobs: 1 (f=1): [m(1)][65.4%][r=900KiB/s,w=1456KiB/s][r=225,w=364 IOPS][eta 01m:4Jobs: 1 (f=1): [m(1)][65.8%][r=932KiB/s,w=1301KiB/s][r=233,w=325 IOPS][eta 01m:4Jobs: 1 (f=1): [m(1)][66.1%][r=904KiB/s,w=1340KiB/s][r=226,w=335 IOPS][eta 01m:4Jobs: 1 (f=1): [m(1)][66.4%][r=872KiB/s,w=1169KiB/s][r=218,w=292 IOPS][eta 01m:4Jobs: 1 (f=1): [m(1)][66.8%][r=916KiB/s,w=1376KiB/s][r=229,w=344 IOPS][eta 01m:4Jobs: 1 (f=1): [m(1)][67.1%][r=936KiB/s,w=1332KiB/s][r=234,w=333 IOPS][eta 01m:3Jobs: 1 (f=1): [m(1)][67.4%][r=924KiB/s,w=1173KiB/s][r=231,w=293 IOPS][eta 01m:3Jobs: 1 (f=1): [m(1)][67.8%][r=888KiB/s,w=1461KiB/s][r=222,w=365 IOPS][eta 01m:3Jobs: 1 (f=1): [m(1)][68.1%][r=880KiB/s,w=1408KiB/s][r=220,w=352 IOPS][eta 01m:3Jobs: 1 (f=1): [m(1)][68.4%][r=868KiB/s,w=1421KiB/s][r=217,w=355 IOPS][eta 01m:3Jobs: 1 (f=1): [m(1)][68.8%][r=928KiB/s,w=1268KiB/s][r=232,w=317 IOPS][eta 01m:3Jobs: 1 (f=1): [m(1)][69.1%][r=844KiB/s,w=1501KiB/s][r=211,w=375 IOPS][eta 01m:3Jobs: 1 (f=1): [m(1)][69.4%][r=900KiB/s,w=1380KiB/s][r=225,w=345 IOPS][eta 01m:3Jobs: 1 (f=1): [m(1)][69.8%][r=924KiB/s,w=1353KiB/s][r=231,w=338 IOPS][eta 01m:3Jobs: 1 (f=1): [m(1)][70.1%][r=956KiB/s,w=1472KiB/s][r=239,w=368 IOPS][eta 01m:3Jobs: 1 (f=1): [m(1)][70.4%][r=908KiB/s,w=1369KiB/s][r=227,w=342 IOPS][eta 01m:2Jobs: 1 (f=1): [m(1)][70.8%][r=928KiB/s,w=1560KiB/s][r=232,w=390 IOPS][eta 01m:2Jobs: 1 (f=1): [m(1)][71.1%][r=880KiB/s,w=1281KiB/s][r=220,w=320 IOPS][eta 01m:2Jobs: 1 (f=1): [m(1)][71.4%][r=964KiB/s,w=1252KiB/s][r=241,w=313 IOPS][eta 01m:2Jobs: 1 (f=1): [m(1)][71.8%][r=880KiB/s,w=1233KiB/s][r=220,w=308 IOPS][eta 01m:2Jobs: 1 (f=1): [m(1)][72.1%][r=912KiB/s,w=1608KiB/s][r=228,w=402 IOPS][eta 01m:2Jobs: 1 (f=1): [m(1)][72.4%][r=916KiB/s,w=1309KiB/s][r=229,w=327 IOPS][eta 01m:2Jobs: 1 (f=1): [m(1)][72.8%][r=924KiB/s,w=1420KiB/s][r=231,w=355 IOPS][eta 01m:2Jobs: 1 (f=1): [m(1)][73.1%][r=920KiB/s,w=1461KiB/s][r=230,w=365 IOPS][eta 01m:2Jobs: 1 (f=1): [m(1)][73.4%][r=940KiB/s,w=1396KiB/s][r=235,w=349 IOPS][eta 01m:2Jobs: 1 (f=1): [m(1)][73.8%][r=848KiB/s,w=1225KiB/s][r=212,w=306 IOPS][eta 01m:1Jobs: 1 (f=1): [m(1)][74.1%][r=916KiB/s,w=1588KiB/s][r=229,w=397 IOPS][eta 01m:1Jobs: 1 (f=1): [m(1)][74.4%][r=896KiB/s,w=1369KiB/s][r=224,w=342 IOPS][eta 01m:1Jobs: 1 (f=1): [m(1)][74.8%][r=896KiB/s,w=1205KiB/s][r=224,w=301 IOPS][eta 01m:1Jobs: 1 (f=1): [m(1)][75.1%][r=928KiB/s,w=1412KiB/s][r=232,w=353 IOPS][eta 01m:1Jobs: 1 (f=1): [m(1)][75.4%][r=944KiB/s,w=1381KiB/s][r=236,w=345 IOPS][eta 01m:1Jobs: 1 (f=1): [m(1)][75.7%][r=932KiB/s,w=1208KiB/s][r=233,w=302 IOPS][eta 01m:1Jobs: 1 (f=1): [m(1)][76.1%][r=948KiB/s,w=1325KiB/s][r=237,w=331 IOPS][eta 01m:1Jobs: 1 (f=1): [m(1)][76.4%][r=940KiB/s,w=1376KiB/s][r=235,w=344 IOPS][eta 01m:1Jobs: 1 (f=1): [m(1)][76.7%][r=960KiB/s,w=1321KiB/s][r=240,w=330 IOPS][eta 01m:1Jobs: 1 (f=1): [m(1)][77.1%][r=968KiB/s,w=1433KiB/s][r=242,w=358 IOPS][eta 01m:0Jobs: 1 (f=1): [m(1)][77.4%][r=908KiB/s,w=1524KiB/s][r=227,w=381 IOPS][eta 01m:0Jobs: 1 (f=1): [m(1)][77.7%][r=912KiB/s,w=1341KiB/s][r=228,w=335 IOPS][eta 01m:0Jobs: 1 (f=1): [m(1)][78.1%][r=888KiB/s,w=1536KiB/s][r=222,w=384 IOPS][eta 01m:0Jobs: 1 (f=1): [m(1)][78.4%][r=940KiB/s,w=1317KiB/s][r=235,w=329 IOPS][eta 01m:0Jobs: 1 (f=1): [m(1)][78.7%][r=976KiB/s,w=1380KiB/s][r=244,w=345 IOPS][eta 01m:0Jobs: 1 (f=1): [m(1)][79.1%][r=880KiB/s,w=1365KiB/s][r=220,w=341 IOPS][eta 01m:0Jobs: 1 (f=1): [m(1)][79.4%][r=892KiB/s,w=1620KiB/s][r=223,w=405 IOPS][eta 01m:0Jobs: 1 (f=1): [m(1)][79.7%][r=904KiB/s,w=1521KiB/s][r=226,w=380 IOPS][eta 01m:0Jobs: 1 (f=1): [m(1)][80.1%][r=888KiB/s,w=1388KiB/s][r=222,w=347 IOPS][eta 01m:0Jobs: 1 (f=1): [m(1)][80.4%][r=944KiB/s,w=1609KiB/s][r=236,w=402 IOPS][eta 00m:5Jobs: 1 (f=1): [m(1)][80.7%][r=924KiB/s,w=1485KiB/s][r=231,w=371 IOPS][eta 00m:5Jobs: 1 (f=1): [m(1)][81.1%][r=924KiB/s,w=1492KiB/s][r=231,w=373 IOPS][eta 00m:5Jobs: 1 (f=1): [m(1)][81.4%][r=936KiB/s,w=1333KiB/s][r=234,w=333 IOPS][eta 00m:5Jobs: 1 (f=1): [m(1)][81.7%][r=956KiB/s,w=1504KiB/s][r=239,w=376 IOPS][eta 00m:5Jobs: 1 (f=1): [m(1)][82.1%][r=940KiB/s,w=1481KiB/s][r=235,w=370 IOPS][eta 00m:5Jobs: 1 (f=1): [m(1)][82.4%][r=912KiB/s,w=1244KiB/s][r=228,w=311 IOPS][eta 00m:5Jobs: 1 (f=1): [m(1)][82.7%][r=1025KiB/s,w=1381KiB/s][r=256,w=345 IOPS][eta 00m:Jobs: 1 (f=1): [m(1)][83.1%][r=936KiB/s,w=1276KiB/s][r=234,w=319 IOPS][eta 00m:5Jobs: 1 (f=1): [m(1)][83.4%][r=984KiB/s,w=1681KiB/s][r=246,w=420 IOPS][eta 00m:5Jobs: 1 (f=1): [m(1)][83.7%][r=932KiB/s,w=1356KiB/s][r=233,w=339 IOPS][eta 00m:4Jobs: 1 (f=1): [m(1)][84.1%][r=916KiB/s,w=1561KiB/s][r=229,w=390 IOPS][eta 00m:4Jobs: 1 (f=1): [m(1)][84.4%][r=952KiB/s,w=1296KiB/s][r=238,w=324 IOPS][eta 00m:4Jobs: 1 (f=1): [m(1)][84.7%][r=948KiB/s,w=1437KiB/s][r=237,w=359 IOPS][eta 00m:4Jobs: 1 (f=1): [m(1)][85.0%][r=1013KiB/s,w=1185KiB/s][r=253,w=296 IOPS][eta 00m:Jobs: 1 (f=1): [m(1)][85.4%][r=920KiB/s,w=1468KiB/s][r=230,w=367 IOPS][eta 00m:4Jobs: 1 (f=1): [m(1)][85.7%][r=960KiB/s,w=1229KiB/s][r=240,w=307 IOPS][eta 00m:4Jobs: 1 (f=1): [m(1)][86.0%][r=956KiB/s,w=1540KiB/s][r=239,w=385 IOPS][eta 00m:4Jobs: 1 (f=1): [m(1)][86.4%][r=932KiB/s,w=1329KiB/s][r=233,w=332 IOPS][eta 00m:4Jobs: 1 (f=1): [m(1)][86.7%][r=900KiB/s,w=1476KiB/s][r=225,w=369 IOPS][eta 00m:4Jobs: 1 (f=1): [m(1)][87.0%][r=940KiB/s,w=1345KiB/s][r=235,w=336 IOPS][eta 00m:3Jobs: 1 (f=1): [m(1)][87.4%][r=940KiB/s,w=1568KiB/s][r=235,w=392 IOPS][eta 00m:3Jobs: 1 (f=1): [m(1)][87.7%][r=912KiB/s,w=1213KiB/s][r=228,w=303 IOPS][eta 00m:3Jobs: 1 (f=1): [m(1)][88.0%][r=916KiB/s,w=1381KiB/s][r=229,w=345 IOPS][eta 00m:3Jobs: 1 (f=1): [m(1)][88.4%][r=908KiB/s,w=1520KiB/s][r=227,w=380 IOPS][eta 00m:3Jobs: 1 (f=1): [m(1)][88.7%][r=916KiB/s,w=1325KiB/s][r=229,w=331 IOPS][eta 00m:3Jobs: 1 (f=1): [m(1)][89.0%][r=896KiB/s,w=1204KiB/s][r=224,w=301 IOPS][eta 00m:3Jobs: 1 (f=1): [m(1)][89.4%][r=888KiB/s,w=1237KiB/s][r=222,w=309 IOPS][eta 00m:3Jobs: 1 (f=1): [m(1)][89.7%][r=916KiB/s,w=1408KiB/s][r=229,w=352 IOPS][eta 00m:3Jobs: 1 (f=1): [m(1)][90.0%][r=948KiB/s,w=1581KiB/s][r=237,w=395 IOPS][eta 00m:3Jobs: 1 (f=1): [m(1)][90.4%][r=956KiB/s,w=1168KiB/s][r=239,w=292 IOPS][eta 00m:2Jobs: 1 (f=1): [m(1)][90.7%][r=956KiB/s,w=1541KiB/s][r=239,w=385 IOPS][eta 00m:2Jobs: 1 (f=1): [m(1)][91.0%][r=936KiB/s,w=1480KiB/s][r=234,w=370 IOPS][eta 00m:2Jobs: 1 (f=1): [m(1)][91.4%][r=896KiB/s,w=1241KiB/s][r=224,w=310 IOPS][eta 00m:2Jobs: 1 (f=1): [m(1)][91.7%][r=984KiB/s,w=1536KiB/s][r=246,w=384 IOPS][eta 00m:2Jobs: 1 (f=1): [m(1)][92.0%][r=980KiB/s,w=1417KiB/s][r=245,w=354 IOPS][eta 00m:2Jobs: 1 (f=1): [m(1)][92.4%][r=976KiB/s,w=1584KiB/s][r=244,w=396 IOPS][eta 00m:2Jobs: 1 (f=1): [m(1)][92.7%][r=956KiB/s,w=1277KiB/s][r=239,w=319 IOPS][eta 00m:2Jobs: 1 (f=1): [m(1)][93.0%][r=960KiB/s,w=1492KiB/s][r=240,w=373 IOPS][eta 00m:2Jobs: 1 (f=1): [m(1)][93.4%][r=912KiB/s,w=1289KiB/s][r=228,w=322 IOPS][eta 00m:2Jobs: 1 (f=1): [m(1)][93.7%][r=904KiB/s,w=1512KiB/s][r=226,w=378 IOPS][eta 00m:1Jobs: 1 (f=1): [m(1)][94.0%][r=964KiB/s,w=1309KiB/s][r=241,w=327 IOPS][eta 00m:1Jobs: 1 (f=1): [m(1)][94.4%][r=928KiB/s,w=1388KiB/s][r=232,w=347 IOPS][eta 00m:1Jobs: 1 (f=1): [m(1)][94.7%][r=944KiB/s,w=1457KiB/s][r=236,w=364 IOPS][eta 00m:1Jobs: 1 (f=1): [m(1)][95.0%][r=976KiB/s,w=1368KiB/s][r=244,w=342 IOPS][eta 00m:1Jobs: 1 (f=1): [m(1)][95.3%][r=932KiB/s,w=1301KiB/s][r=233,w=325 IOPS][eta 00m:1Jobs: 1 (f=1): [m(1)][95.7%][r=976KiB/s,w=1440KiB/s][r=244,w=360 IOPS][eta 00m:1Jobs: 1 (f=1): [m(1)][96.0%][r=908KiB/s,w=1477KiB/s][r=227,w=369 IOPS][eta 00m:1Jobs: 1 (f=1): [m(1)][96.3%][r=940KiB/s,w=1300KiB/s][r=235,w=325 IOPS][eta 00m:1Jobs: 1 (f=1): [m(1)][96.7%][r=920KiB/s,w=1617KiB/s][r=230,w=404 IOPS][eta 00m:1Jobs: 1 (f=1): [m(1)][97.0%][r=892KiB/s,w=1144KiB/s][r=223,w=286 IOPS][eta 00m:0Jobs: 1 (f=1): [m(1)][97.3%][r=944KiB/s,w=1325KiB/s][r=236,w=331 IOPS][eta 00m:0Jobs: 1 (f=1): [m(1)][97.7%][r=888KiB/s,w=1624KiB/s][r=222,w=406 IOPS][eta 00m:0Jobs: 1 (f=1): [m(1)][98.0%][r=956KiB/s,w=1417KiB/s][r=239,w=354 IOPS][eta 00m:0Jobs: 1 (f=1): [m(1)][98.3%][r=956KiB/s,w=1537KiB/s][r=239,w=384 IOPS][eta 00m:0Jobs: 1 (f=1): [m(1)][98.7%][r=940KiB/s,w=1644KiB/s][r=235,w=411 IOPS][eta 00m:0Jobs: 1 (f=1): [m(1)][99.0%][r=976KiB/s,w=1469KiB/s][r=244,w=367 IOPS][eta 00m:0Jobs: 1 (f=1): [m(1)][99.3%][r=924KiB/s,w=1296KiB/s][r=231,w=324 IOPS][eta 00m:0Jobs: 1 (f=1): [m(1)][99.7%][r=948KiB/s,w=1097KiB/s][r=237,w=274 IOPS][eta 00m:0Jobs: 1 (f=1): [m(1)][100.0%][r=912KiB/s,w=1368KiB/s][r=228,w=342 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=9981: Sun Oct  8 09:07:26 2017
   read: IOPS=229, BW=918KiB/s (940kB/s)(269MiB/300039msec)
    slat (usec): min=3, max=8807, avg=25.85, stdev=62.01
    clat (usec): min=409, max=154352, avg=16076.01, stdev=8950.17
     lat (usec): min=431, max=154366, avg=16102.28, stdev=8950.59
    clat percentiles (usec):
     |  1.00th=[   611],  5.00th=[  4555], 10.00th=[  7439], 20.00th=[  9765],
     | 30.00th=[ 11469], 40.00th=[ 13042], 50.00th=[ 14484], 60.00th=[ 16319],
     | 70.00th=[ 18482], 80.00th=[ 21627], 90.00th=[ 26608], 95.00th=[ 31589],
     | 99.00th=[ 45876], 99.50th=[ 53740], 99.90th=[ 74974], 99.95th=[ 86508],
     | 99.99th=[124257]
   bw (  KiB/s): min=  776, max= 1080, per=100.00%, avg=918.10, stdev=49.10, samples=600
   iops        : min=  194, max=  270, avg=229.52, stdev=12.27, samples=600
  write: IOPS=344, BW=1376KiB/s (1409kB/s)(403MiB/300039msec)
    slat (usec): min=4, max=6194, avg=25.74, stdev=40.04
    clat (nsec): min=1555, max=28763k, avg=851316.88, stdev=673333.18
     lat (usec): min=444, max=28785, avg=877.47, stdev=677.09
    clat percentiles (usec):
     |  1.00th=[  515],  5.00th=[  545], 10.00th=[  570], 20.00th=[  603],
     | 30.00th=[  635], 40.00th=[  660], 50.00th=[  701], 60.00th=[  734],
     | 70.00th=[  791], 80.00th=[  873], 90.00th=[ 1106], 95.00th=[ 1549],
     | 99.00th=[ 4293], 99.50th=[ 5800], 99.90th=[ 8029], 99.95th=[ 9503],
     | 99.99th=[11994]
   bw (  KiB/s): min=  872, max= 2016, per=100.00%, avg=1376.67, stdev=176.44, samples=600
   iops        : min=  218, max=  504, avg=344.16, stdev=44.11, samples=600
  lat (usec)   : 2=0.01%, 50=0.01%, 500=0.36%, 750=37.92%, 1000=14.76%
  lat (msec)   : 2=6.64%, 4=1.52%, 10=7.37%, 20=21.43%, 50=9.73%
  lat (msec)   : 100=0.26%, 250=0.01%
  cpu          : usr=0.52%, sys=1.88%, ctx=165802, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=68859,103247,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=918KiB/s (940kB/s), 918KiB/s-918KiB/s (940kB/s-940kB/s), io=269MiB (282MB), run=300039-300039msec
  WRITE: bw=1376KiB/s (1409kB/s), 1376KiB/s-1376KiB/s (1409kB/s-1409kB/s), io=403MiB (423MB), run=300039-300039msec

Disk stats (read/write):
  sda: ios=69260/103380, merge=0/100, ticks=1107608/87644, in_queue=1195188, util=100.00%
```

*file-size*
```
ls -al test4K-rw-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  8 09:07 test4K-rw-aio
```

## vultr - 488M
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            225M     0  225M   0% /dev
tmpfs            49M  5.6M   44M  12% /run
/dev/vda1        20G  7.9G   11G  43% /
tmpfs           245M     0  245M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           245M     0  245M   0% /sys/fs/cgroup
tmpfs            49M     0   49M   0% /run/user/901
```

*rw*
```
./fio --filename=test4K-rw-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randrw --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G --rwmixread=40
myjob: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [m(1)][6.5%][r=36.7MiB/s,w=56.2MiB/s][r=9390,w=14.4k IOPS][eta 00Jobs: 1 (f=1): [m(1)][8.7%][r=35.5MiB/s,w=53.5MiB/s][r=9083,w=13.7k IOPS][eta 00Jobs: 1 (f=1): [m(1)][10.9%][r=37.4MiB/s,w=55.2MiB/s][r=9568,w=14.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][13.0%][r=36.6MiB/s,w=54.0MiB/s][r=9369,w=14.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][15.6%][r=38.5MiB/s,w=58.1MiB/s][r=9844,w=14.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][17.8%][r=36.8MiB/s,w=55.1MiB/s][r=9410,w=14.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][20.0%][r=36.0MiB/s,w=52.8MiB/s][r=9221,w=13.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][21.7%][r=35.5MiB/s,w=52.0MiB/s][r=9078,w=13.3k IOPS][eta 0Jobs: 1 (f=1): [m(1)][24.4%][r=36.8MiB/s,w=55.0MiB/s][r=9414,w=14.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][26.7%][r=37.4MiB/s,w=55.7MiB/s][r=9578,w=14.3k IOPS][eta 0Jobs: 1 (f=1): [m(1)][28.9%][r=35.9MiB/s,w=52.8MiB/s][r=9191,w=13.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][30.4%][r=36.7MiB/s,w=53.9MiB/s][r=9384,w=13.8k IOPS][eta 0Jobs: 1 (f=1): [m(1)][33.3%][r=36.6MiB/s,w=55.2MiB/s][r=9380,w=14.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][35.6%][r=36.0MiB/s,w=56.0MiB/s][r=9465,w=14.3k IOPS][eta 0Jobs: 1 (f=1): [m(1)][37.8%][r=37.7MiB/s,w=57.3MiB/s][r=9640,w=14.7k IOPS][eta 0Jobs: 1 (f=1): [m(1)][40.0%][r=36.4MiB/s,w=54.3MiB/s][r=9310,w=13.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][42.2%][r=37.1MiB/s,w=55.7MiB/s][r=9504,w=14.3k IOPS][eta 0Jobs: 1 (f=1): [m(1)][44.4%][r=36.2MiB/s,w=54.9MiB/s][r=9280,w=14.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][46.7%][r=36.4MiB/s,w=54.6MiB/s][r=9315,w=13.0k IOPS][eta 0Jobs: 1 (f=1): [m(1)][48.9%][r=35.2MiB/s,w=52.8MiB/s][r=9002,w=13.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][51.1%][r=37.4MiB/s,w=55.7MiB/s][r=9569,w=14.3k IOPS][eta 0Jobs: 1 (f=1): [m(1)][53.3%][r=37.0MiB/s,w=54.7MiB/s][r=9477,w=14.0k IOPS][eta 0Jobs: 1 (f=1): [m(1)][55.6%][r=35.7MiB/s,w=52.6MiB/s][r=9129,w=13.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][57.8%][r=35.4MiB/s,w=52.0MiB/s][r=9068,w=13.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][60.0%][r=37.0MiB/s,w=56.2MiB/s][r=9480,w=14.4k IOPS][eta 0Jobs: 1 (f=1): [m(1)][62.2%][r=35.1MiB/s,w=53.4MiB/s][r=8974,w=13.7k IOPS][eta 0Jobs: 1 (f=1): [m(1)][64.4%][r=38.2MiB/s,w=56.8MiB/s][r=9786,w=14.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][66.7%][r=37.1MiB/s,w=55.1MiB/s][r=9489,w=14.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][68.9%][r=36.4MiB/s,w=55.2MiB/s][r=9309,w=14.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][71.1%][r=37.3MiB/s,w=56.5MiB/s][r=9547,w=14.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][73.3%][r=37.7MiB/s,w=58.6MiB/s][r=9660,w=14.0k IOPS][eta 0Jobs: 1 (f=1): [m(1)][75.6%][r=37.3MiB/s,w=56.0MiB/s][r=9553,w=14.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][77.8%][r=36.8MiB/s,w=54.3MiB/s][r=9429,w=13.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][80.0%][r=36.4MiB/s,w=54.0MiB/s][r=9308,w=13.8k IOPS][eta 0Jobs: 1 (f=1): [m(1)][82.2%][r=38.3MiB/s,w=56.8MiB/s][r=9814,w=14.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][84.4%][r=34.6MiB/s,w=53.5MiB/s][r=8848,w=13.7k IOPS][eta 0Jobs: 1 (f=1): [m(1)][86.7%][r=34.5MiB/s,w=51.1MiB/s][r=8828,w=13.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][88.9%][r=34.6MiB/s,w=51.0MiB/s][r=8866,w=13.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][91.1%][r=34.0MiB/s,w=52.9MiB/s][r=8956,w=13.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][93.3%][r=37.0MiB/s,w=55.0MiB/s][r=9476,w=14.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][95.6%][r=35.3MiB/s,w=52.9MiB/s][r=9027,w=13.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][97.8%][r=37.7MiB/s,w=56.5MiB/s][r=9662,w=14.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][100.0%][r=38.1MiB/s,w=57.9MiB/s][r=9758,w=14.8k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=26958: Sun Oct  8 09:02:38 2017
   read: IOPS=9346, BW=36.5MiB/s (38.3MB/s)(1638MiB/44873msec)
    slat (nsec): min=1415, max=574535, avg=7450.55, stdev=5572.02
    clat (usec): min=26, max=15363, avg=248.91, stdev=198.44
     lat (usec): min=132, max=15367, avg=256.74, stdev=198.48
    clat percentiles (usec):
     |  1.00th=[  147],  5.00th=[  157], 10.00th=[  167], 20.00th=[  180],
     | 30.00th=[  190], 40.00th=[  200], 50.00th=[  212], 60.00th=[  225],
     | 70.00th=[  241], 80.00th=[  265], 90.00th=[  318], 95.00th=[  388],
     | 99.00th=[ 1254], 99.50th=[ 1663], 99.90th=[ 2114], 99.95th=[ 2245],
     | 99.99th=[ 4555]
   bw (  KiB/s): min=33595, max=40984, per=100.00%, avg=37404.07, stdev=1398.11, samples=89
   iops        : min= 8398, max=10246, avg=9351.00, stdev=349.55, samples=89
  write: IOPS=14.0k, BW=54.8MiB/s (57.4MB/s)(2458MiB/44873msec)
    slat (nsec): min=1703, max=1188.2k, avg=8169.21, stdev=6305.60
    clat (nsec): min=1006, max=15215k, avg=102703.65, stdev=70318.15
     lat (usec): min=45, max=15221, avg=111.27, stdev=70.53
    clat percentiles (usec):
     |  1.00th=[   52],  5.00th=[   58], 10.00th=[   63], 20.00th=[   71],
     | 30.00th=[   77], 40.00th=[   84], 50.00th=[   91], 60.00th=[   99],
     | 70.00th=[  111], 80.00th=[  125], 90.00th=[  151], 95.00th=[  186],
     | 99.00th=[  281], 99.50th=[  322], 99.90th=[  523], 99.95th=[  734],
     | 99.99th=[ 1876]
   bw (  KiB/s): min=50320, max=62504, per=100.00%, avg=56090.97, stdev=2254.49, samples=89
   iops        : min=12580, max=15626, avg=14022.74, stdev=563.62, samples=89
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.01%, 50=0.32%
  lat (usec)   : 100=36.16%, 250=52.34%, 500=10.02%, 750=0.35%, 1000=0.21%
  lat (msec)   : 2=0.51%, 4=0.07%, 10=0.01%, 20=0.01%
  cpu          : usr=6.56%, sys=25.99%, ctx=634829, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=419426,629150,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=36.5MiB/s (38.3MB/s), 36.5MiB/s-36.5MiB/s (38.3MB/s-38.3MB/s), io=1638MiB (1718MB), run=44873-44873msec
  WRITE: bw=54.8MiB/s (57.4MB/s), 54.8MiB/s-54.8MiB/s (57.4MB/s-57.4MB/s), io=2458MiB (2577MB), run=44873-44873msec

Disk stats (read/write):
  vda: ios=418244/627314, merge=0/8, ticks=98100/60868, in_queue=158720, util=99.19%
```

*file-size*
```
ls -al test4K-rw-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  8 09:02 test4K-rw-aio
```

## linode - 989M
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        20G  1.3G   18G   7% /
devtmpfs        493M     0  493M   0% /dev
tmpfs           495M     0  495M   0% /dev/shm
tmpfs           495M  7.7M  488M   2% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           495M     0  495M   0% /sys/fs/cgroup
tmpfs            99M     0   99M   0% /run/user/901
```

*rw*
```
./fio --filename=test4K-rw-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randrw --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G --rwmixread=40
myjob: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [m(1)][9.1%][r=55.7MiB/s,w=85.6MiB/s][r=14.3k,w=21.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][12.5%][r=53.4MiB/s,w=80.6MiB/s][r=13.7k,w=20.6k IOPS][eta Jobs: 1 (f=1): [m(1)][15.6%][r=55.4MiB/s,w=82.7MiB/s][r=14.2k,w=21.2k IOPS][eta Jobs: 1 (f=1): [m(1)][18.8%][r=50.6MiB/s,w=75.6MiB/s][r=12.0k,w=19.4k IOPS][eta Jobs: 1 (f=1): [m(1)][21.9%][r=49.8MiB/s,w=74.9MiB/s][r=12.7k,w=19.2k IOPS][eta Jobs: 1 (f=1): [m(1)][25.0%][r=53.3MiB/s,w=79.6MiB/s][r=13.7k,w=20.4k IOPS][eta Jobs: 1 (f=1): [m(1)][28.1%][r=52.7MiB/s,w=78.5MiB/s][r=13.5k,w=20.1k IOPS][eta Jobs: 1 (f=1): [m(1)][32.3%][r=53.0MiB/s,w=79.1MiB/s][r=13.8k,w=20.2k IOPS][eta Jobs: 1 (f=1): [m(1)][35.5%][r=53.0MiB/s,w=79.4MiB/s][r=13.6k,w=20.3k IOPS][eta Jobs: 1 (f=1): [m(1)][38.7%][r=53.3MiB/s,w=80.2MiB/s][r=13.6k,w=20.5k IOPS][eta Jobs: 1 (f=1): [m(1)][41.9%][r=52.7MiB/s,w=78.7MiB/s][r=13.5k,w=20.1k IOPS][eta Jobs: 1 (f=1): [m(1)][45.2%][r=50.8MiB/s,w=75.7MiB/s][r=13.0k,w=19.4k IOPS][eta Jobs: 1 (f=1): [m(1)][48.4%][r=51.4MiB/s,w=77.1MiB/s][r=13.2k,w=19.7k IOPS][eta Jobs: 1 (f=1): [m(1)][51.6%][r=53.6MiB/s,w=80.2MiB/s][r=13.7k,w=20.5k IOPS][eta Jobs: 1 (f=1): [m(1)][54.8%][r=50.6MiB/s,w=76.3MiB/s][r=12.9k,w=19.5k IOPS][eta Jobs: 1 (f=1): [m(1)][58.1%][r=49.3MiB/s,w=74.4MiB/s][r=12.6k,w=19.1k IOPS][eta Jobs: 1 (f=1): [m(1)][61.3%][r=55.6MiB/s,w=83.1MiB/s][r=14.2k,w=21.3k IOPS][eta Jobs: 1 (f=1): [m(1)][64.5%][r=50.3MiB/s,w=75.4MiB/s][r=12.9k,w=19.3k IOPS][eta Jobs: 1 (f=1): [m(1)][65.6%][r=33.9MiB/s,w=50.8MiB/s][r=8674,w=12.0k IOPS][eta 0Jobs: 1 (f=1): [m(1)][68.8%][r=49.2MiB/s,w=73.2MiB/s][r=12.6k,w=18.7k IOPS][eta Jobs: 1 (f=1): [m(1)][71.9%][r=53.9MiB/s,w=81.3MiB/s][r=13.8k,w=20.8k IOPS][eta Jobs: 1 (f=1): [m(1)][75.0%][r=56.4MiB/s,w=84.6MiB/s][r=14.4k,w=21.7k IOPS][eta Jobs: 1 (f=1): [m(1)][80.6%][r=55.5MiB/s,w=83.0MiB/s][r=14.2k,w=21.3k IOPS][eta Jobs: 1 (f=1): [m(1)][83.9%][r=53.1MiB/s,w=80.4MiB/s][r=13.6k,w=20.6k IOPS][eta Jobs: 1 (f=1): [m(1)][87.1%][r=56.0MiB/s,w=83.3MiB/s][r=14.3k,w=21.3k IOPS][eta Jobs: 1 (f=1): [m(1)][90.3%][r=55.9MiB/s,w=83.3MiB/s][r=14.3k,w=21.3k IOPS][eta Jobs: 1 (f=1): [m(1)][93.5%][r=55.3MiB/s,w=83.1MiB/s][r=14.1k,w=21.3k IOPS][eta Jobs: 1 (f=1): [m(1)][96.8%][r=57.4MiB/s,w=85.6MiB/s][r=14.7k,w=21.9k IOPS][eta Jobs: 1 (f=1): [m(1)][100.0%][r=50.3MiB/s,w=75.0MiB/s][r=12.9k,w=19.5k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16914: Sun Oct  8 09:01:12 2017
   read: IOPS=13.4k, BW=52.3MiB/s (54.9MB/s)(1639MiB/31300msec)
    slat (usec): min=2, max=1261, avg= 7.86, stdev=10.93
    clat (nsec): min=1039, max=11726k, avg=106844.51, stdev=70772.77
     lat (usec): min=47, max=11736, avg=115.09, stdev=71.96
    clat percentiles (usec):
     |  1.00th=[   54],  5.00th=[   67], 10.00th=[   74], 20.00th=[   82],
     | 30.00th=[   88], 40.00th=[   94], 50.00th=[  100], 60.00th=[  108],
     | 70.00th=[  116], 80.00th=[  126], 90.00th=[  143], 95.00th=[  159],
     | 99.00th=[  219], 99.50th=[  265], 99.90th=[  627], 99.95th=[ 1074],
     | 99.99th=[ 3752]
   bw (  KiB/s): min=30904, max=62616, per=99.79%, avg=53493.73, stdev=4870.25, samples=62
   iops        : min= 7726, max=15654, avg=13373.42, stdev=1217.57, samples=62
  write: IOPS=20.1k, BW=78.5MiB/s (82.3MB/s)(2457MiB/31300msec)
    slat (usec): min=2, max=1338, avg= 8.98, stdev=11.70
    clat (nsec): min=1424, max=11477k, avg=109860.23, stdev=70062.93
     lat (usec): min=49, max=11631, avg=119.26, stdev=72.94
    clat percentiles (usec):
     |  1.00th=[   57],  5.00th=[   70], 10.00th=[   77], 20.00th=[   85],
     | 30.00th=[   91], 40.00th=[   97], 50.00th=[  102], 60.00th=[  110],
     | 70.00th=[  118], 80.00th=[  128], 90.00th=[  145], 95.00th=[  163],
     | 99.00th=[  225], 99.50th=[  281], 99.90th=[  742], 99.95th=[ 1172],
     | 99.99th=[ 3556]
   bw (  KiB/s): min=46120, max=92752, per=99.80%, avg=80237.94, stdev=7211.24, samples=62
   iops        : min=11530, max=23188, avg=20059.47, stdev=1802.82, samples=62
  lat (usec)   : 2=0.01%, 20=0.02%, 50=0.58%, 100=47.04%, 250=51.70%
  lat (usec)   : 500=0.49%, 750=0.08%, 1000=0.03%
  lat (msec)   : 2=0.04%, 4=0.02%, 10=0.01%, 20=0.01%
  cpu          : usr=7.75%, sys=31.44%, ctx=268674, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=419466,629110,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=52.3MiB/s (54.9MB/s), 52.3MiB/s-52.3MiB/s (54.9MB/s-54.9MB/s), io=1639MiB (1718MB), run=31300-31300msec
  WRITE: bw=78.5MiB/s (82.3MB/s), 78.5MiB/s-78.5MiB/s (82.3MB/s-82.3MB/s), io=2457MiB (2577MB), run=31300-31300msec

Disk stats (read/write):
  sda: ios=415964/623975, merge=0/4, ticks=21997/48810, in_queue=81533, util=93.27%
```

*file-size*
```
ls -al test4K-rw-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  8 09:01 test4K-rw-aio
```

## upcloud - 992M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            477M     0  477M   0% /dev
tmpfs           100M  5.4M   94M   6% /run
/dev/vda1        30G  1.8G   27G   7% /
tmpfs           497M     0  497M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           497M     0  497M   0% /sys/fs/cgroup
tmpfs           100M     0  100M   0% /run/user/901
```

*rw*
```
./fio --filename=test4K-rw-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randrw --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G --rwmixread=40
myjob: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [m(1)][7.1%][r=62.3MiB/s,w=93.2MiB/s][r=15.0k,w=23.8k IOPS][eta 0Jobs: 1 (f=1): [m(1)][12.9%][r=47.4MiB/s,w=71.3MiB/s][r=12.1k,w=18.3k IOPS][eta Jobs: 1 (f=1): [m(1)][16.7%][r=63.4MiB/s,w=93.9MiB/s][r=16.2k,w=24.0k IOPS][eta Jobs: 1 (f=1): [m(1)][20.7%][r=61.9MiB/s,w=92.0MiB/s][r=15.8k,w=23.8k IOPS][eta Jobs: 1 (f=1): [m(1)][22.6%][r=33.5MiB/s,w=49.6MiB/s][r=8567,w=12.7k IOPS][eta 0Jobs: 1 (f=1): [m(1)][25.8%][r=50.1MiB/s,w=74.9MiB/s][r=12.8k,w=19.2k IOPS][eta Jobs: 1 (f=1): [m(1)][28.1%][r=48.5MiB/s,w=72.3MiB/s][r=12.4k,w=18.5k IOPS][eta Jobs: 1 (f=1): [m(1)][32.3%][r=58.3MiB/s,w=89.1MiB/s][r=14.9k,w=22.8k IOPS][eta Jobs: 1 (f=1): [m(1)][33.3%][r=61.3MiB/s,w=91.9MiB/s][r=15.7k,w=23.5k IOPS][eta Jobs: 1 (f=1): [m(1)][37.5%][r=32.4MiB/s,w=48.3MiB/s][r=8305,w=12.4k IOPS][eta 0Jobs: 1 (f=1): [m(1)][40.6%][r=55.9MiB/s,w=82.7MiB/s][r=14.3k,w=21.2k IOPS][eta Jobs: 1 (f=1): [m(1)][43.8%][r=59.7MiB/s,w=89.4MiB/s][r=15.3k,w=22.9k IOPS][eta Jobs: 1 (f=1): [m(1)][48.4%][r=62.5MiB/s,w=92.6MiB/s][r=16.0k,w=23.7k IOPS][eta Jobs: 1 (f=1): [m(1)][51.6%][r=57.8MiB/s,w=86.9MiB/s][r=14.8k,w=22.2k IOPS][eta Jobs: 1 (f=1): [m(1)][53.1%][r=28.5MiB/s,w=43.7MiB/s][r=7303,w=11.2k IOPS][eta 0Jobs: 1 (f=1): [m(1)][56.2%][r=50.4MiB/s,w=75.4MiB/s][r=12.9k,w=19.3k IOPS][eta Jobs: 1 (f=1): [m(1)][59.4%][r=53.4MiB/s,w=79.8MiB/s][r=13.7k,w=20.4k IOPS][eta Jobs: 1 (f=1): [m(1)][62.5%][r=60.2MiB/s,w=90.6MiB/s][r=15.4k,w=23.2k IOPS][eta Jobs: 1 (f=1): [m(1)][65.6%][r=55.7MiB/s,w=83.6MiB/s][r=14.2k,w=21.4k IOPS][eta Jobs: 1 (f=1): [m(1)][68.8%][r=29.7MiB/s,w=43.3MiB/s][r=7590,w=11.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][71.9%][r=48.4MiB/s,w=72.0MiB/s][r=12.4k,w=18.4k IOPS][eta Jobs: 1 (f=1): [m(1)][75.0%][r=50.1MiB/s,w=75.5MiB/s][r=12.8k,w=19.3k IOPS][eta Jobs: 1 (f=1): [m(1)][78.1%][r=61.7MiB/s,w=93.3MiB/s][r=15.8k,w=23.9k IOPS][eta Jobs: 1 (f=1): [m(1)][81.2%][r=58.5MiB/s,w=88.9MiB/s][r=14.0k,w=22.8k IOPS][eta Jobs: 1 (f=1): [m(1)][84.4%][r=29.5MiB/s,w=45.4MiB/s][r=7541,w=11.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][87.5%][r=52.0MiB/s,w=78.5MiB/s][r=13.6k,w=20.1k IOPS][eta Jobs: 1 (f=1): [m(1)][90.6%][r=50.0MiB/s,w=75.4MiB/s][r=13.0k,w=19.3k IOPS][eta Jobs: 1 (f=1): [m(1)][93.8%][r=61.2MiB/s,w=93.0MiB/s][r=15.7k,w=23.8k IOPS][eta Jobs: 1 (f=1): [m(1)][96.9%][r=62.3MiB/s,w=93.5MiB/s][r=15.9k,w=23.9k IOPS][eta Jobs: 1 (f=1): [m(1)][100.0%][r=35.4MiB/s,w=53.2MiB/s][r=9065,w=13.6k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=21635: Sun Oct  8 09:01:30 2017
   read: IOPS=13.2k, BW=51.6MiB/s (54.1MB/s)(1638MiB/31762msec)
    slat (nsec): min=1302, max=257884, avg=3190.11, stdev=1480.40
    clat (usec): min=6, max=400427, avg=82.36, stdev=1438.49
     lat (usec): min=39, max=400428, avg=85.71, stdev=1438.49
    clat percentiles (usec):
     |  1.00th=[   50],  5.00th=[   56], 10.00th=[   60], 20.00th=[   64],
     | 30.00th=[   68], 40.00th=[   71], 50.00th=[   74], 60.00th=[   77],
     | 70.00th=[   81], 80.00th=[   86], 90.00th=[   94], 95.00th=[  103],
     | 99.00th=[  135], 99.50th=[  194], 99.90th=[  330], 99.95th=[  594],
     | 99.99th=[ 1401]
   bw (  KiB/s): min= 4224, max=65384, per=100.00%, avg=52829.75, stdev=14972.56, samples=63
   iops        : min= 1056, max=16346, avg=13207.43, stdev=3743.14, samples=63
  write: IOPS=19.8k, BW=77.4MiB/s (81.1MB/s)(2458MiB/31762msec)
    slat (nsec): min=1430, max=122690, avg=3571.43, stdev=1447.25
    clat (usec): min=18, max=461461, avg=139.82, stdev=2170.78
     lat (usec): min=66, max=461463, avg=143.56, stdev=2170.82
    clat percentiles (usec):
     |  1.00th=[   84],  5.00th=[   92], 10.00th=[   97], 20.00th=[  103],
     | 30.00th=[  110], 40.00th=[  115], 50.00th=[  121], 60.00th=[  127],
     | 70.00th=[  135], 80.00th=[  143], 90.00th=[  155], 95.00th=[  169],
     | 99.00th=[  269], 99.50th=[  326], 99.90th=[  824], 99.95th=[ 1074],
     | 99.99th=[ 2376]
   bw (  KiB/s): min= 5856, max=97864, per=99.98%, avg=79212.67, stdev=22655.35, samples=63
   iops        : min= 1464, max=24466, avg=19803.16, stdev=5663.83, samples=63
  lat (usec)   : 10=0.01%, 20=0.01%, 50=0.40%, 100=46.08%, 250=52.69%
  lat (usec)   : 500=0.69%, 750=0.06%, 1000=0.04%
  lat (msec)   : 2=0.04%, 4=0.01%, 10=0.01%, 50=0.01%, 100=0.01%
  lat (msec)   : 250=0.01%, 500=0.01%
  cpu          : usr=4.56%, sys=15.73%, ctx=666375, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=419447,629129,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=51.6MiB/s (54.1MB/s), 51.6MiB/s-51.6MiB/s (54.1MB/s-54.1MB/s), io=1638MiB (1718MB), run=31762-31762msec
  WRITE: bw=77.4MiB/s (81.1MB/s), 77.4MiB/s-77.4MiB/s (81.1MB/s-81.1MB/s), io=2458MiB (2577MB), run=31762-31762msec

Disk stats (read/write):
  vda: ios=416377/624403, merge=0/6, ticks=32896/87772, in_queue=120580, util=99.69%
```

*file-size*
```
ls -al test4K-rw-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  8 09:01 test4K-rw-aio
```

## ovh sg - 1024M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            476M     0  476M   0% /dev
tmpfs            97M  3.0M   94M   4% /run
/dev/sda1        30G  1.5G   28G   6% /
tmpfs           485M     0  485M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           485M     0  485M   0% /sys/fs/cgroup
tmpfs            97M     0   97M   0% /run/user/901
```

*rw*
```
./fio --filename=test4K-rw-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randrw --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G --rwmixread=40
myjob: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [m(1)][7.1%][r=41.1MiB/s,w=62.2MiB/s][r=10.5k,w=15.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][9.8%][r=42.0MiB/s,w=61.0MiB/s][r=10.8k,w=15.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][12.2%][r=42.1MiB/s,w=62.2MiB/s][r=10.8k,w=15.9k IOPS][eta Jobs: 1 (f=1): [m(1)][14.6%][r=42.3MiB/s,w=62.0MiB/s][r=10.8k,w=15.9k IOPS][eta Jobs: 1 (f=1): [m(1)][17.5%][r=42.4MiB/s,w=63.2MiB/s][r=10.9k,w=16.2k IOPS][eta Jobs: 1 (f=1): [m(1)][20.0%][r=40.8MiB/s,w=61.7MiB/s][r=10.4k,w=15.8k IOPS][eta Jobs: 1 (f=1): [m(1)][22.5%][r=43.6MiB/s,w=63.4MiB/s][r=11.2k,w=16.2k IOPS][eta Jobs: 1 (f=1): [m(1)][25.0%][r=42.6MiB/s,w=63.0MiB/s][r=10.9k,w=16.1k IOPS][eta Jobs: 1 (f=1): [m(1)][27.5%][r=40.9MiB/s,w=62.8MiB/s][r=10.5k,w=16.1k IOPS][eta Jobs: 1 (f=1): [m(1)][30.0%][r=40.0MiB/s,w=61.7MiB/s][r=10.2k,w=15.8k IOPS][eta Jobs: 1 (f=1): [m(1)][32.5%][r=41.6MiB/s,w=62.5MiB/s][r=10.7k,w=16.0k IOPS][eta Jobs: 1 (f=1): [m(1)][35.0%][r=41.5MiB/s,w=61.9MiB/s][r=10.6k,w=15.8k IOPS][eta Jobs: 1 (f=1): [m(1)][37.5%][r=41.7MiB/s,w=62.5MiB/s][r=10.7k,w=16.0k IOPS][eta Jobs: 1 (f=1): [m(1)][40.0%][r=40.2MiB/s,w=59.3MiB/s][r=10.3k,w=15.2k IOPS][eta Jobs: 1 (f=1): [m(1)][42.5%][r=40.0MiB/s,w=61.6MiB/s][r=10.5k,w=15.8k IOPS][eta Jobs: 1 (f=1): [m(1)][45.0%][r=41.7MiB/s,w=61.0MiB/s][r=10.7k,w=15.9k IOPS][eta Jobs: 1 (f=1): [m(1)][47.5%][r=41.4MiB/s,w=62.4MiB/s][r=10.6k,w=15.0k IOPS][eta Jobs: 1 (f=1): [m(1)][50.0%][r=41.7MiB/s,w=62.8MiB/s][r=10.7k,w=16.1k IOPS][eta Jobs: 1 (f=1): [m(1)][52.5%][r=41.1MiB/s,w=62.9MiB/s][r=10.5k,w=16.1k IOPS][eta Jobs: 1 (f=1): [m(1)][55.0%][r=41.1MiB/s,w=62.3MiB/s][r=10.5k,w=15.9k IOPS][eta Jobs: 1 (f=1): [m(1)][57.5%][r=40.1MiB/s,w=61.6MiB/s][r=10.3k,w=15.8k IOPS][eta Jobs: 1 (f=1): [m(1)][60.0%][r=41.1MiB/s,w=61.1MiB/s][r=10.5k,w=15.6k IOPS][eta Jobs: 1 (f=1): [m(1)][62.5%][r=41.4MiB/s,w=62.6MiB/s][r=10.6k,w=16.0k IOPS][eta Jobs: 1 (f=1): [m(1)][65.0%][r=41.3MiB/s,w=62.6MiB/s][r=10.6k,w=16.0k IOPS][eta Jobs: 1 (f=1): [m(1)][67.5%][r=42.4MiB/s,w=64.6MiB/s][r=10.8k,w=16.5k IOPS][eta Jobs: 1 (f=1): [m(1)][70.0%][r=43.3MiB/s,w=63.4MiB/s][r=11.1k,w=16.2k IOPS][eta Jobs: 1 (f=1): [m(1)][72.5%][r=42.1MiB/s,w=63.8MiB/s][r=10.8k,w=16.3k IOPS][eta Jobs: 1 (f=1): [m(1)][75.0%][r=41.7MiB/s,w=62.8MiB/s][r=10.7k,w=16.1k IOPS][eta Jobs: 1 (f=1): [m(1)][77.5%][r=40.0MiB/s,w=61.2MiB/s][r=10.5k,w=15.7k IOPS][eta Jobs: 1 (f=1): [m(1)][80.0%][r=39.3MiB/s,w=59.8MiB/s][r=10.1k,w=15.3k IOPS][eta Jobs: 1 (f=1): [m(1)][82.5%][r=40.1MiB/s,w=61.0MiB/s][r=10.3k,w=15.6k IOPS][eta Jobs: 1 (f=1): [m(1)][85.0%][r=41.5MiB/s,w=61.6MiB/s][r=10.6k,w=15.8k IOPS][eta Jobs: 1 (f=1): [m(1)][87.5%][r=42.3MiB/s,w=64.3MiB/s][r=10.8k,w=16.5k IOPS][eta Jobs: 1 (f=1): [m(1)][90.0%][r=41.3MiB/s,w=62.5MiB/s][r=10.6k,w=15.0k IOPS][eta Jobs: 1 (f=1): [m(1)][92.5%][r=42.7MiB/s,w=65.2MiB/s][r=10.9k,w=16.7k IOPS][eta Jobs: 1 (f=1): [m(1)][95.0%][r=41.7MiB/s,w=62.0MiB/s][r=10.7k,w=15.9k IOPS][eta Jobs: 1 (f=1): [m(1)][97.5%][r=40.6MiB/s,w=60.5MiB/s][r=10.4k,w=15.5k IOPS][eta Jobs: 1 (f=1): [m(1)][100.0%][r=41.5MiB/s,w=62.4MiB/s][r=10.6k,w=15.0k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=15002: Mon Nov 27 15:46:48 2017
   read: IOPS=10.6k, BW=41.4MiB/s (43.4MB/s)(1637MiB/39525msec)
    slat (nsec): min=1517, max=1009.0k, avg=4517.67, stdev=3028.67
    clat (usec): min=32, max=5245, avg=215.49, stdev=202.34
     lat (usec): min=75, max=5247, avg=220.17, stdev=202.39
    clat percentiles (usec):
     |  1.00th=[  130],  5.00th=[  139], 10.00th=[  145], 20.00th=[  153],
     | 30.00th=[  161], 40.00th=[  169], 50.00th=[  178], 60.00th=[  190],
     | 70.00th=[  202], 80.00th=[  219], 90.00th=[  247], 95.00th=[  281],
     | 99.00th=[ 1401], 99.50th=[ 1795], 99.90th=[ 2409], 99.95th=[ 2540],
     | 99.99th=[ 2737]
   bw (  KiB/s): min=38120, max=45264, per=100.00%, avg=42403.85, stdev=1229.55, samples=79
   iops        : min= 9530, max=11316, avg=10600.96, stdev=307.39, samples=79
  write: IOPS=15.9k, BW=62.2MiB/s (65.2MB/s)(2459MiB/39525msec)
    slat (nsec): min=1714, max=343818, avg=4889.53, stdev=2822.07
    clat (usec): min=20, max=2621, avg=98.04, stdev=46.67
     lat (usec): min=49, max=2626, avg=103.10, stdev=46.72
    clat percentiles (usec):
     |  1.00th=[   55],  5.00th=[   60], 10.00th=[   64], 20.00th=[   69],
     | 30.00th=[   74], 40.00th=[   80], 50.00th=[   87], 60.00th=[   98],
     | 70.00th=[  112], 80.00th=[  124], 90.00th=[  147], 95.00th=[  165],
     | 99.00th=[  204], 99.50th=[  225], 99.90th=[  494], 99.95th=[ 1012],
     | 99.99th=[ 1467]
   bw (  KiB/s): min=56928, max=67944, per=100.00%, avg=63716.91, stdev=1746.15, samples=79
   iops        : min=14232, max=16986, avg=15929.23, stdev=436.54, samples=79
  lat (usec)   : 50=0.06%, 100=37.02%, 250=59.12%, 500=2.57%, 750=0.29%
  lat (usec)   : 1000=0.21%
  lat (msec)   : 2=0.59%, 4=0.12%, 10=0.01%
  cpu          : usr=3.71%, sys=18.50%, ctx=838612, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=419003,629573,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=41.4MiB/s (43.4MB/s), 41.4MiB/s-41.4MiB/s (43.4MB/s-43.4MB/s), io=1637MiB (1716MB), run=39525-39525msec
  WRITE: bw=62.2MiB/s (65.2MB/s), 62.2MiB/s-62.2MiB/s (65.2MB/s-65.2MB/s), io=2459MiB (2579MB), run=39525-39525msec

Disk stats (read/write):
  sda: ios=418336/628584, merge=0/7, ticks=88632/60944, in_queue=149468, util=99.74%
```

*file-size*
```
ls -al test4K-rw-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Nov 27 15:46 test4K-rw-aio
```

## itldc lax - 992M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            479M     0  479M   0% /dev
tmpfs           100M  3.0M   97M   3% /run
/dev/vda2       9.5G  1.9G  7.2G  21% /
tmpfs           497M     0  497M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           497M     0  497M   0% /sys/fs/cgroup
```

*rw*
```
./fio --filename=test4K-rw-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randrw --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G --rwmixread=40
myjob: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [m(1)][16.7%][r=97.0MiB/s,w=145MiB/s][r=24.8k,w=37.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][23.5%][r=110MiB/s,w=164MiB/s][r=28.2k,w=42.1k IOPS][eta 00Jobs: 1 (f=1): [m(1)][31.2%][r=129MiB/s,w=191MiB/s][r=32.0k,w=48.8k IOPS][eta 00Jobs: 1 (f=1): [m(1)][40.0%][r=129MiB/s,w=194MiB/s][r=33.1k,w=49.6k IOPS][eta 00Jobs: 1 (f=1): [m(1)][46.7%][r=127MiB/s,w=192MiB/s][r=32.6k,w=49.1k IOPS][eta 00Jobs: 1 (f=1): [m(1)][53.3%][r=130MiB/s,w=195MiB/s][r=33.2k,w=49.8k IOPS][eta 00Jobs: 1 (f=1): [m(1)][64.3%][r=130MiB/s,w=195MiB/s][r=33.3k,w=50.0k IOPS][eta 00Jobs: 1 (f=1): [m(1)][71.4%][r=131MiB/s,w=196MiB/s][r=33.6k,w=50.3k IOPS][eta 00Jobs: 1 (f=1): [m(1)][78.6%][r=129MiB/s,w=194MiB/s][r=33.1k,w=49.7k IOPS][eta 00Jobs: 1 (f=1): [m(1)][85.7%][r=128MiB/s,w=192MiB/s][r=32.8k,w=49.1k IOPS][eta 00Jobs: 1 (f=1): [m(1)][92.9%][r=129MiB/s,w=193MiB/s][r=32.9k,w=49.4k IOPS][eta 00Jobs: 1 (f=1): [m(1)][100.0%][r=110MiB/s,w=165MiB/s][r=28.2k,w=42.3k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2223: Mon Nov 27 06:46:32 2017
   read: IOPS=31.2k, BW=122MiB/s (128MB/s)(1640MiB/13439msec)
    slat (nsec): min=1267, max=2568.4k, avg=3762.56, stdev=6147.95
    clat (nsec): min=565, max=13867k, avg=44885.30, stdev=59279.47
     lat (usec): min=17, max=13869, avg=48.89, stdev=59.86
    clat percentiles (usec):
     |  1.00th=[   21],  5.00th=[   25], 10.00th=[   27], 20.00th=[   31],
     | 30.00th=[   34], 40.00th=[   37], 50.00th=[   41], 60.00th=[   45],
     | 70.00th=[   50], 80.00th=[   56], 90.00th=[   66], 95.00th=[   75],
     | 99.00th=[  106], 99.50th=[  133], 99.90th=[  243], 99.95th=[  338],
     | 99.99th=[ 1254]
   bw (  KiB/s): min=94124, max=146355, per=99.94%, avg=124863.85, stdev=13735.12, samples=26
   iops        : min=23531, max=36588, avg=31215.88, stdev=3433.75, samples=26
  write: IOPS=46.8k, BW=183MiB/s (192MB/s)(2456MiB/13439msec)
    slat (nsec): min=1625, max=9626.8k, avg=4394.83, stdev=12866.15
    clat (nsec): min=888, max=14492k, avg=46476.10, stdev=52801.51
     lat (usec): min=16, max=14497, avg=51.11, stdev=54.91
    clat percentiles (usec):
     |  1.00th=[   22],  5.00th=[   26], 10.00th=[   29], 20.00th=[   32],
     | 30.00th=[   36], 40.00th=[   39], 50.00th=[   43], 60.00th=[   46],
     | 70.00th=[   51], 80.00th=[   58], 90.00th=[   68], 95.00th=[   78],
     | 99.00th=[  112], 99.50th=[  141], 99.90th=[  297], 99.95th=[  424],
     | 99.99th=[ 1172]
   bw (  KiB/s): min=143887, max=218251, per=99.95%, avg=187067.69, stdev=20512.76, samples=26
   iops        : min=35971, max=54562, avg=46766.81, stdev=5128.23, samples=26
  lat (nsec)   : 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 10=0.01%, 20=0.42%, 50=69.30%, 100=28.91%
  lat (usec)   : 250=1.25%, 500=0.08%, 750=0.02%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.01%
  cpu          : usr=11.46%, sys=43.37%, ctx=266654, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=419766,628810,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=122MiB/s (128MB/s), 122MiB/s-122MiB/s (128MB/s-128MB/s), io=1640MiB (1719MB), run=13439-13439msec
  WRITE: bw=183MiB/s (192MB/s), 183MiB/s-183MiB/s (192MB/s-192MB/s), io=2456MiB (2576MB), run=13439-13439msec

Disk stats (read/write):
  vda: ios=419054/627767, merge=0/2, ticks=13316/27300, in_queue=40504, util=91.65%
```

*file-size*
```
ls -al test4K-rw-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Nov 27 06:46 test4K-rw-aio
```

## impactvps ovz - 1024M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/simfs       15G  1.1G   14G   7% /
devtmpfs        512M     0  512M   0% /dev
tmpfs           512M     0  512M   0% /dev/shm
tmpfs           512M  6.7M  506M   2% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           512M     0  512M   0% /sys/fs/cgroup
tmpfs           103M     0  103M   0% /run/user/901
```

*rw*
```
./fio --filename=test4K-rw-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randrw --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G --rwmixread=40
myjob: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [m(1)][3.2%][r=18.6MiB/s,w=28.1MiB/s][r=4750,w=7190 IOPS][eta 01mJobs: 1 (f=1): [m(1)][4.2%][r=16.7MiB/s,w=25.1MiB/s][r=4269,w=6427 IOPS][eta 01mJobs: 1 (f=1): [m(1)][5.4%][r=19.6MiB/s,w=28.5MiB/s][r=5013,w=7303 IOPS][eta 01mJobs: 1 (f=1): [m(1)][6.7%][r=21.2MiB/s,w=31.9MiB/s][r=5418,w=8157 IOPS][eta 01mJobs: 1 (f=1): [m(1)][8.0%][r=19.9MiB/s,w=30.4MiB/s][r=5102,w=7776 IOPS][eta 01mJobs: 1 (f=1): [m(1)][9.0%][r=17.1MiB/s,w=26.4MiB/s][r=4373,w=6750 IOPS][eta 01mJobs: 1 (f=1): [m(1)][10.6%][r=25.0MiB/s,w=36.7MiB/s][r=6403,w=9405 IOPS][eta 01Jobs: 1 (f=1): [m(1)][12.0%][r=23.6MiB/s,w=34.4MiB/s][r=6053,w=8815 IOPS][eta 01Jobs: 1 (f=1): [m(1)][13.1%][r=19.0MiB/s,w=27.8MiB/s][r=4870,w=7128 IOPS][eta 01Jobs: 1 (f=1): [m(1)][14.3%][r=20.4MiB/s,w=30.2MiB/s][r=5215,w=7719 IOPS][eta 01Jobs: 1 (f=1): [m(1)][14.4%][r=2080KiB/s,w=3016KiB/s][r=520,w=754 IOPS][eta 01m:Jobs: 1 (f=1): [m(1)][14.9%][r=9785KiB/s,w=13.7MiB/s][r=2446,w=3497 IOPS][eta 01Jobs: 1 (f=1): [m(1)][14.9%][r=40KiB/s,w=64KiB/s][r=10,w=16 IOPS][eta 01m:26s]  Jobs: 1 (f=1): [m(1)][14.8%][r=2040KiB/s,w=3264KiB/s][r=510,w=816 IOPS][eta 01m:Jobs: 1 (f=1): [m(1)][16.4%][r=25.3MiB/s,w=37.0MiB/s][r=6473,w=9725 IOPS][eta 01Jobs: 1 (f=1): [m(1)][17.2%][r=14.4MiB/s,w=22.3MiB/s][r=3695,w=5717 IOPS][eta 01Jobs: 1 (f=1): [m(1)][18.1%][r=12.8MiB/s,w=18.9MiB/s][r=3275,w=4829 IOPS][eta 01Jobs: 1 (f=1): [m(1)][19.6%][r=25.2MiB/s,w=37.6MiB/s][r=6444,w=9631 IOPS][eta 01Jobs: 1 (f=1): [m(1)][21.3%][r=26.3MiB/s,w=39.4MiB/s][r=6732,w=10.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][22.9%][r=26.5MiB/s,w=40.8MiB/s][r=6772,w=10.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][24.5%][r=26.4MiB/s,w=40.3MiB/s][r=6748,w=10.3k IOPS][eta 0Jobs: 1 (f=1): [m(1)][25.5%][r=17.1MiB/s,w=26.0MiB/s][r=4366,w=6665 IOPS][eta 01Jobs: 1 (f=1): [m(1)][27.0%][r=22.0MiB/s,w=33.2MiB/s][r=5638,w=8504 IOPS][eta 01Jobs: 1 (f=1): [m(1)][28.0%][r=19.6MiB/s,w=28.8MiB/s][r=5023,w=7361 IOPS][eta 01Jobs: 1 (f=1): [m(1)][28.4%][r=4868KiB/s,w=6826KiB/s][r=1217,w=1706 IOPS][eta 01Jobs: 1 (f=1): [m(1)][28.3%][r=84KiB/s,w=236KiB/s][r=21,w=59 IOPS][eta 01m:16s] Jobs: 1 (f=1): [m(1)][28.4%][r=1241KiB/s,w=1985KiB/s][r=310,w=496 IOPS][eta 01m:Jobs: 1 (f=1): [m(1)][29.1%][r=10.7MiB/s,w=16.4MiB/s][r=2750,w=4199 IOPS][eta 01Jobs: 1 (f=1): [m(1)][29.2%][r=3364KiB/s,w=4964KiB/s][r=841,w=1241 IOPS][eta 01mJobs: 1 (f=1): [m(1)][29.8%][r=10.1MiB/s,w=15.2MiB/s][r=2581,w=3889 IOPS][eta 01Jobs: 1 (f=1): [m(1)][31.5%][r=25.3MiB/s,w=39.0MiB/s][r=6476,w=9990 IOPS][eta 01Jobs: 1 (f=1): [m(1)][32.7%][r=23.5MiB/s,w=35.5MiB/s][r=6008,w=9085 IOPS][eta 01Jobs: 1 (f=1): [m(1)][34.6%][r=27.9MiB/s,w=41.2MiB/s][r=7153,w=10.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][36.2%][r=27.7MiB/s,w=41.3MiB/s][r=7098,w=10.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][37.9%][r=29.0MiB/s,w=43.8MiB/s][r=7432,w=11.2k IOPS][eta 0Jobs: 1 (f=1): [m(1)][39.6%][r=26.0MiB/s,w=40.0MiB/s][r=6910,w=10.2k IOPS][eta 0Jobs: 1 (f=1): [m(1)][41.0%][r=21.5MiB/s,w=32.8MiB/s][r=5503,w=8395 IOPS][eta 00Jobs: 1 (f=1): [m(1)][42.4%][r=23.8MiB/s,w=35.6MiB/s][r=6094,w=9105 IOPS][eta 00Jobs: 1 (f=1): [m(1)][42.6%][r=1632KiB/s,w=2708KiB/s][r=408,w=677 IOPS][eta 00m:Jobs: 1 (f=1): [m(1)][42.7%][r=104KiB/s,w=192KiB/s][r=26,w=48 IOPS][eta 00m:59s]Jobs: 1 (f=1): [m(1)][43.3%][r=10.5MiB/s,w=16.6MiB/s][r=2681,w=4244 IOPS][eta 00Jobs: 1 (f=1): [m(1)][43.8%][r=10.2MiB/s,w=14.6MiB/s][r=2603,w=3743 IOPS][eta 00Jobs: 1 (f=1): [m(1)][43.9%][r=52KiB/s,w=92KiB/s][r=13,w=23 IOPS][eta 01m:00s]  Jobs: 1 (f=1): [m(1)][44.4%][r=9984KiB/s,w=14.2MiB/s][r=2496,w=3640 IOPS][eta 01Jobs: 1 (f=1): [m(1)][46.2%][r=30.8MiB/s,w=46.2MiB/s][r=7879,w=11.8k IOPS][eta 0Jobs: 1 (f=1): [m(1)][48.1%][r=26.8MiB/s,w=39.9MiB/s][r=6871,w=10.2k IOPS][eta 0Jobs: 1 (f=1): [m(1)][49.5%][r=24.0MiB/s,w=35.0MiB/s][r=6155,w=8972 IOPS][eta 00Jobs: 1 (f=1): [m(1)][51.0%][r=30.3MiB/s,w=45.3MiB/s][r=7750,w=11.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][52.0%][r=16.6MiB/s,w=25.2MiB/s][r=4257,w=6448 IOPS][eta 00Jobs: 1 (f=1): [m(1)][54.0%][r=32.8MiB/s,w=49.5MiB/s][r=8399,w=12.7k IOPS][eta 0Jobs: 1 (f=1): [m(1)][56.1%][r=32.9MiB/s,w=48.8MiB/s][r=8423,w=12.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][57.1%][r=18.0MiB/s,w=28.4MiB/s][r=4858,w=7280 IOPS][eta 00Jobs: 1 (f=1): [m(1)][58.2%][r=12.3MiB/s,w=18.4MiB/s][r=3157,w=4703 IOPS][eta 00Jobs: 1 (f=1): [m(1)][58.0%][r=848KiB/s,w=1185KiB/s][r=212,w=296 IOPS][eta 00m:4Jobs: 1 (f=1): [m(1)][57.8%][r=48KiB/s,w=32KiB/s][r=12,w=8 IOPS][eta 00m:43s]   Jobs: 1 (f=1): [m(1)][58.8%][r=9117KiB/s,w=13.8MiB/s][r=2279,w=3524 IOPS][eta 00Jobs: 1 (f=1): [m(1)][58.7%][r=160KiB/s,w=324KiB/s][r=40,w=81 IOPS][eta 00m:43s]Jobs: 1 (f=1): [m(1)][59.0%][r=5796KiB/s,w=8856KiB/s][r=1449,w=2214 IOPS][eta 00Jobs: 1 (f=1): [m(1)][60.0%][r=20.7MiB/s,w=31.1MiB/s][r=5288,w=7955 IOPS][eta 00Jobs: 1 (f=1): [m(1)][62.1%][r=34.6MiB/s,w=52.6MiB/s][r=8869,w=13.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][64.4%][r=37.1MiB/s,w=56.8MiB/s][r=9492,w=14.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][66.7%][r=35.3MiB/s,w=53.3MiB/s][r=9043,w=13.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][69.1%][r=32.3MiB/s,w=49.7MiB/s][r=8261,w=12.7k IOPS][eta 0Jobs: 1 (f=1): [m(1)][70.8%][r=38.1MiB/s,w=57.2MiB/s][r=9762,w=14.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][72.6%][r=24.1MiB/s,w=35.7MiB/s][r=6164,w=9132 IOPS][eta 00Jobs: 1 (f=1): [m(1)][72.9%][r=104KiB/s,w=128KiB/s][r=26,w=32 IOPS][eta 00m:26s]Jobs: 1 (f=1): [m(1)][72.4%][r=1269KiB/s,w=2022KiB/s][r=317,w=505 IOPS][eta 00m:Jobs: 1 (f=1): [m(1)][73.5%][r=8068KiB/s,w=11.7MiB/s][r=2017,w=2990 IOPS][eta 00Jobs: 1 (f=1): [m(1)][73.0%][r=304KiB/s,w=416KiB/s][r=76,w=104 IOPS][eta 00m:27sJobs: 1 (f=1): [m(1)][73.3%][r=228KiB/s,w=388KiB/s][r=57,w=97 IOPS][eta 00m:27s]Jobs: 1 (f=1): [m(1)][73.5%][r=496KiB/s,w=756KiB/s][r=124,w=189 IOPS][eta 00m:27Jobs: 1 (f=1): [m(1)][75.2%][r=32.5MiB/s,w=48.1MiB/s][r=8315,w=12.3k IOPS][eta 0Jobs: 1 (f=1): [m(1)][77.0%][r=31.8MiB/s,w=47.3MiB/s][r=8140,w=12.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][79.6%][r=36.6MiB/s,w=53.6MiB/s][r=9359,w=13.7k IOPS][eta 0Jobs: 1 (f=1): [m(1)][81.4%][r=41.0MiB/s,w=62.1MiB/s][r=10.5k,w=15.9k IOPS][eta Jobs: 1 (f=1): [m(1)][84.2%][r=43.5MiB/s,w=66.6MiB/s][r=11.1k,w=17.0k IOPS][eta Jobs: 1 (f=1): [m(1)][86.2%][r=30.8MiB/s,w=47.0MiB/s][r=7895,w=12.0k IOPS][eta 0Jobs: 1 (f=1): [m(1)][87.2%][r=18.5MiB/s,w=28.3MiB/s][r=4745,w=7252 IOPS][eta 00Jobs: 1 (f=1): [m(1)][87.4%][r=204KiB/s,w=384KiB/s][r=51,w=96 IOPS][eta 00m:12s]Jobs: 1 (f=1): [m(1)][87.6%][r=924KiB/s,w=1164KiB/s][r=231,w=291 IOPS][eta 00m:1Jobs: 1 (f=1): [m(1)][87.8%][r=0KiB/s,w=0KiB/s][r=0,w=0 IOPS][eta 00m:12s]      Jobs: 1 (f=1): [m(1)][87.9%][r=2588KiB/s,w=4200KiB/s][r=647,w=1050 IOPS][eta 00mJobs: 1 (f=1): [m(1)][88.9%][r=14.5MiB/s,w=22.0MiB/s][r=3718,w=5637 IOPS][eta 00Jobs: 1 (f=1): [m(1)][90.8%][r=43.0MiB/s,w=63.5MiB/s][r=11.0k,w=16.3k IOPS][eta Jobs: 1 (f=1): [m(1)][93.8%][r=41.1MiB/s,w=62.2MiB/s][r=10.5k,w=15.9k IOPS][eta Jobs: 1 (f=1): [m(1)][96.8%][r=44.9MiB/s,w=67.8MiB/s][r=11.5k,w=17.3k IOPS][eta Jobs: 1 (f=1): [m(1)][98.9%][r=44.7MiB/s,w=68.9MiB/s][r=11.4k,w=17.6k IOPS][eta 00m:01s]
myjob: (groupid=0, jobs=1): err= 0: pid=28166: Mon Nov 27 15:20:24 2017
   read: IOPS=4556, BW=17.8MiB/s (18.7MB/s)(1636MiB/91927msec)
    slat (nsec): min=1237, max=1164.1M, avg=197822.03, stdev=5118277.34
    clat (usec): min=7, max=1207.0k, avg=261.68, stdev=5738.29
     lat (usec): min=9, max=1207.4k, avg=459.71, stdev=7980.28
    clat percentiles (usec):
     |  1.00th=[    11],  5.00th=[    13], 10.00th=[    15], 20.00th=[    17],
     | 30.00th=[    21], 40.00th=[    30], 50.00th=[   147], 60.00th=[   155],
     | 70.00th=[   163], 80.00th=[   210], 90.00th=[   302], 95.00th=[   404],
     | 99.00th=[   873], 99.50th=[  1844], 99.90th=[ 20055], 99.95th=[ 44303],
     | 99.99th=[202376]
   bw (  KiB/s): min=   16, max=50104, per=100.00%, avg=18903.90, stdev=14260.20, samples=177
   iops        : min=    4, max=12526, avg=4725.95, stdev=3565.07, samples=177
  write: IOPS=6849, BW=26.8MiB/s (28.1MB/s)(2460MiB/91927msec)
    slat (nsec): min=1847, max=223751k, avg=12232.91, stdev=679728.79
    clat (nsec): min=1105, max=1206.0M, avg=264549.20, stdev=5971923.42
     lat (usec): min=6, max=1206.0k, avg=276.86, stdev=6026.59
    clat percentiles (usec):
     |  1.00th=[    11],  5.00th=[    13], 10.00th=[    14], 20.00th=[    16],
     | 30.00th=[    18], 40.00th=[    24], 50.00th=[   145], 60.00th=[   153],
     | 70.00th=[   161], 80.00th=[   200], 90.00th=[   297], 95.00th=[   400],
     | 99.00th=[   832], 99.50th=[  1778], 99.90th=[ 20317], 99.95th=[ 45876],
     | 99.99th=[252707]
   bw (  KiB/s): min=   40, max=75160, per=100.00%, avg=28418.84, stdev=21488.67, samples=177
   iops        : min=   10, max=18790, avg=7104.69, stdev=5372.18, samples=177
  lat (usec)   : 2=0.01%, 10=0.80%, 20=32.11%, 50=9.08%, 100=0.20%
  lat (usec)   : 250=38.47%, 500=16.75%, 750=1.34%, 1000=0.47%
  lat (msec)   : 2=0.31%, 4=0.05%, 10=0.28%, 20=0.05%, 50=0.06%
  lat (msec)   : 100=0.02%, 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2000=0.01%
  cpu          : usr=1.55%, sys=12.18%, ctx=275148, majf=0, minf=34
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=418889,629687,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=17.8MiB/s (18.7MB/s), 17.8MiB/s-17.8MiB/s (18.7MB/s-18.7MB/s), io=1636MiB (1716MB), run=91927-91927msec
  WRITE: bw=26.8MiB/s (28.1MB/s), 26.8MiB/s-26.8MiB/s (28.1MB/s-28.1MB/s), io=2460MiB (2579MB), run=91927-91927msec
```

*file-size*
```
ls -al test4K-rw-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Nov 27 15:20 test4K-rw-aio
```

## launchvps lax - 2000M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            981M     0  981M   0% /dev
tmpfs           201M  3.1M  197M   2% /run
/dev/vda1        28G  1.9G   25G   8% /
tmpfs          1001M     0 1001M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs          1001M     0 1001M   0% /sys/fs/cgroup
tmpfs           201M     0  201M   0% /run/user/901
```

*rw*
```
./fio --filename=test4K-rw-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randrw --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G --rwmixread=40
myjob: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [m(1)][3.9%][r=29.2MiB/s,w=44.3MiB/s][r=7466,w=11.3k IOPS][eta 01Jobs: 1 (f=1): [m(1)][10.0%][r=82.6MiB/s,w=124MiB/s][r=21.1k,w=31.7k IOPS][eta 0Jobs: 1 (f=1): [m(1)][16.1%][r=85.7MiB/s,w=129MiB/s][r=21.9k,w=32.0k IOPS][eta 0Jobs: 1 (f=1): [m(1)][21.4%][r=86.9MiB/s,w=132MiB/s][r=22.3k,w=33.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][21.2%][r=3692KiB/s,w=5384KiB/s][r=923,w=1346 IOPS][eta 00mJobs: 1 (f=1): [m(1)][21.1%][r=0KiB/s,w=0KiB/s][r=0,w=0 IOPS][eta 00m:30s]      Jobs: 1 (f=1): [m(1)][21.7%][r=30.1MiB/s,w=45.2MiB/s][r=7705,w=11.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][22.5%][r=13.7MiB/s,w=20.4MiB/s][r=3508,w=5230 IOPS][eta 00Jobs: 1 (f=1): [m(1)][23.6%][r=18.1MiB/s,w=27.0MiB/s][r=4634,w=6919 IOPS][eta 00Jobs: 1 (f=1): [m(1)][25.4%][r=27.8MiB/s,w=42.7MiB/s][r=7113,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][28.4%][r=49.0MiB/s,w=74.1MiB/s][r=12.8k,w=18.0k IOPS][eta Jobs: 1 (f=1): [m(1)][28.2%][r=24KiB/s,w=32KiB/s][r=6,w=8 IOPS][eta 00m:51s]    Jobs: 1 (f=1): [m(1)][28.4%][r=5337KiB/s,w=7675KiB/s][r=1334,w=1918 IOPS][eta 00Jobs: 1 (f=1): [m(1)][31.4%][r=50.7MiB/s,w=74.9MiB/s][r=12.0k,w=19.2k IOPS][eta Jobs: 1 (f=1): [m(1)][31.5%][r=32KiB/s,w=56KiB/s][r=8,w=14 IOPS][eta 00m:50s]   Jobs: 1 (f=1): [m(1)][32.0%][r=6560KiB/s,w=9.80MiB/s][r=1640,w=2510 IOPS][eta 00Jobs: 1 (f=1): [m(1)][33.8%][r=31.4MiB/s,w=45.5MiB/s][r=8041,w=11.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][35.1%][r=25.1MiB/s,w=37.4MiB/s][r=6437,w=9584 IOPS][eta 00Jobs: 1 (f=1): [m(1)][35.1%][r=24KiB/s,w=36KiB/s][r=6,w=9 IOPS][eta 00m:50s]    Jobs: 1 (f=1): [m(1)][35.4%][r=4788KiB/s,w=7152KiB/s][r=1197,w=1788 IOPS][eta 00Jobs: 1 (f=1): [m(1)][37.7%][r=35.9MiB/s,w=53.7MiB/s][r=9190,w=13.7k IOPS][eta 0Jobs: 1 (f=1): [m(1)][38.0%][r=2996KiB/s,w=4324KiB/s][r=749,w=1081 IOPS][eta 00mJobs: 1 (f=1): [m(1)][38.8%][r=17.9MiB/s,w=27.4MiB/s][r=4578,w=7012 IOPS][eta 00Jobs: 1 (f=1): [m(1)][39.0%][r=5952KiB/s,w=8392KiB/s][r=1488,w=2098 IOPS][eta 00Jobs: 1 (f=1): [m(1)][40.2%][r=15.1MiB/s,w=22.5MiB/s][r=3862,w=5749 IOPS][eta 00Jobs: 1 (f=1): [m(1)][42.0%][r=28.1MiB/s,w=42.3MiB/s][r=7196,w=10.8k IOPS][eta 0Jobs: 1 (f=1): [m(1)][44.9%][r=44.7MiB/s,w=67.2MiB/s][r=11.4k,w=17.2k IOPS][eta Jobs: 1 (f=1): [m(1)][50.7%][r=98.8MiB/s,w=148MiB/s][r=25.3k,w=37.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][50.7%][r=52KiB/s,w=40KiB/s][r=13,w=10 IOPS][eta 00m:36s]  Jobs: 1 (f=1): [m(1)][50.6%][r=1084KiB/s,w=1532KiB/s][r=271,w=383 IOPS][eta 00m:Jobs: 1 (f=1): [m(1)][53.2%][r=36.4MiB/s,w=54.9MiB/s][r=9316,w=14.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][54.4%][r=25.8MiB/s,w=39.2MiB/s][r=6599,w=10.0k IOPS][eta 0Jobs: 1 (f=1): [m(1)][54.3%][r=652KiB/s,w=1053KiB/s][r=163,w=263 IOPS][eta 00m:3Jobs: 1 (f=1): [m(1)][57.0%][r=37.4MiB/s,w=56.4MiB/s][r=9585,w=14.4k IOPS][eta 0Jobs: 1 (f=1): [m(1)][57.5%][r=13.9MiB/s,w=21.6MiB/s][r=3567,w=5523 IOPS][eta 00Jobs: 1 (f=1): [m(1)][58.8%][r=13.6MiB/s,w=20.6MiB/s][r=3493,w=5264 IOPS][eta 00Jobs: 1 (f=1): [m(1)][60.8%][r=34.0MiB/s,w=52.4MiB/s][r=8947,w=13.4k IOPS][eta 0Jobs: 1 (f=1): [m(1)][60.5%][r=152KiB/s,w=244KiB/s][r=38,w=61 IOPS][eta 00m:32s]Jobs: 1 (f=1): [m(1)][62.5%][r=35.4MiB/s,w=52.8MiB/s][r=9056,w=13.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][63.0%][r=8KiB/s,w=0KiB/s][r=2,w=0 IOPS][eta 00m:30s]      Jobs: 1 (f=1): [m(1)][64.2%][r=29.3MiB/s,w=44.4MiB/s][r=7489,w=11.4k IOPS][eta 0Jobs: 1 (f=1): [m(1)][67.1%][r=39.1MiB/s,w=58.8MiB/s][r=10.0k,w=15.1k IOPS][eta Jobs: 1 (f=1): [m(1)][70.1%][r=45.8MiB/s,w=68.8MiB/s][r=11.7k,w=17.6k IOPS][eta Jobs: 1 (f=1): [m(1)][71.4%][r=22.8MiB/s,w=33.8MiB/s][r=5843,w=8650 IOPS][eta 00Jobs: 1 (f=1): [m(1)][70.9%][r=0KiB/s,w=0KiB/s][r=0,w=0 IOPS][eta 00m:23s]      Jobs: 1 (f=1): [m(1)][71.6%][r=13.5MiB/s,w=19.7MiB/s][r=3452,w=5053 IOPS][eta 00Jobs: 1 (f=1): [m(1)][73.8%][r=38.1MiB/s,w=56.4MiB/s][r=9742,w=14.4k IOPS][eta 0Jobs: 1 (f=1): [m(1)][75.9%][r=26.6MiB/s,w=41.5MiB/s][r=6809,w=10.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][78.2%][r=32.0MiB/s,w=48.7MiB/s][r=8446,w=12.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][77.5%][r=4KiB/s,w=12KiB/s][r=1,w=3 IOPS][eta 00m:18s]     Jobs: 1 (f=1): [m(1)][78.0%][r=9989KiB/s,w=15.0MiB/s][r=2497,w=3840 IOPS][eta 00Jobs: 1 (f=1): [m(1)][79.3%][r=11.8MiB/s,w=17.3MiB/s][r=3010,w=4430 IOPS][eta 00Jobs: 1 (f=1): [m(1)][82.5%][r=60.8MiB/s,w=91.2MiB/s][r=15.6k,w=23.4k IOPS][eta Jobs: 1 (f=1): [m(1)][84.8%][r=25.3MiB/s,w=37.9MiB/s][r=6481,w=9708 IOPS][eta 00Jobs: 1 (f=1): [m(1)][84.0%][r=0KiB/s,w=0KiB/s][r=0,w=0 IOPS][eta 00m:13s]      Jobs: 1 (f=1): [m(1)][84.5%][r=9.85MiB/s,w=14.5MiB/s][r=2522,w=3705 IOPS][eta 00Jobs: 1 (f=1): [m(1)][87.8%][r=52.7MiB/s,w=79.5MiB/s][r=13.5k,w=20.4k IOPS][eta Jobs: 1 (f=1): [m(1)][88.0%][r=0KiB/s,w=0KiB/s][r=0,w=0 IOPS][eta 00m:10s]      Jobs: 1 (f=1): [m(1)][88.4%][r=932KiB/s,w=1548KiB/s][r=233,w=387 IOPS][eta 00m:1Jobs: 1 (f=1): [m(1)][88.5%][r=12.3MiB/s,w=18.1MiB/s][r=3160,w=4629 IOPS][eta 00Jobs: 1 (f=1): [m(1)][89.7%][r=15.1MiB/s,w=22.2MiB/s][r=3878,w=5682 IOPS][eta 00Jobs: 1 (f=1): [m(1)][90.8%][r=25.0MiB/s,w=36.7MiB/s][r=6403,w=9396 IOPS][eta 00Jobs: 1 (f=1): [m(1)][93.0%][r=35.6MiB/s,w=53.4MiB/s][r=9122,w=13.7k IOPS][eta 0Jobs: 1 (f=1): [m(1)][95.3%][r=23.7MiB/s,w=34.5MiB/s][r=6064,w=8820 IOPS][eta 00Jobs: 1 (f=1): [m(1)][95.3%][r=8KiB/s,w=4KiB/s][r=2,w=1 IOPS][eta 00m:04s]      Jobs: 1 (f=1): [m(1)][96.5%][r=21.4MiB/s,w=31.7MiB/s][r=5478,w=8103 IOPS][eta 00Jobs: 1 (f=1): [m(1)][96.6%][r=8260KiB/s,w=12.1MiB/s][r=2065,w=3098 IOPS][eta 00Jobs: 1 (f=1): [m(1)][97.7%][r=15.9MiB/s,w=23.1MiB/s][r=4081,w=5902 IOPS][eta 00Jobs: 1 (f=1): [m(1)][100.0%][r=35.8MiB/s,w=53.5MiB/s][r=9169,w=13.7k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=6984: Tue Nov 28 09:42:28 2017
   read: IOPS=4920, BW=19.2MiB/s (20.2MB/s)(1640MiB/85339msec)
    slat (nsec): min=1160, max=2483.0k, avg=4735.54, stdev=6495.00
    clat (nsec): min=430, max=7082.3M, avg=736064.88, stdev=32114138.75
     lat (usec): min=13, max=7082.3k, avg=741.00, stdev=32114.28
    clat percentiles (usec):
     |  1.00th=[     19],  5.00th=[     22], 10.00th=[     24],
     | 20.00th=[     28], 30.00th=[     31], 40.00th=[     35],
     | 50.00th=[     40], 60.00th=[     46], 70.00th=[     58],
     | 80.00th=[    206], 90.00th=[    334], 95.00th=[   1516],
     | 99.00th=[   5735], 99.50th=[   8848], 99.90th=[  20317],
     | 99.95th=[  32637], 99.99th=[1451230]
   bw (  KiB/s): min=    8, max=116376, per=100.00%, avg=26227.14, stdev=26615.54, samples=127
   iops        : min=    2, max=29094, avg=6556.76, stdev=6653.90, samples=127
  write: IOPS=7366, BW=28.8MiB/s (30.2MB/s)(2456MiB/85339msec)
    slat (nsec): min=1347, max=1896.6k, avg=5168.89, stdev=5351.04
    clat (nsec): min=352, max=36718k, avg=40880.47, stdev=115948.51
     lat (usec): min=12, max=36793, avg=46.26, stdev=116.25
    clat percentiles (usec):
     |  1.00th=[   19],  5.00th=[   22], 10.00th=[   24], 20.00th=[   28],
     | 30.00th=[   30], 40.00th=[   33], 50.00th=[   36], 60.00th=[   39],
     | 70.00th=[   43], 80.00th=[   48], 90.00th=[   57], 95.00th=[   66],
     | 99.00th=[  114], 99.50th=[  165], 99.90th=[  529], 99.95th=[  898],
     | 99.99th=[ 2278]
   bw (  KiB/s): min=    8, max=175568, per=100.00%, avg=40217.19, stdev=40000.81, samples=124
   iops        : min=    2, max=43892, avg=10054.28, stdev=10000.25, samples=124
  lat (nsec)   : 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=2.52%, 50=73.46%
  lat (usec)   : 100=13.21%, 250=5.77%, 500=1.57%, 750=0.54%, 1000=0.35%
  lat (msec)   : 2=0.93%, 4=0.98%, 10=0.50%, 20=0.12%, 50=0.03%
  lat (msec)   : 100=0.01%, 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2000=0.01%, >=2000=0.01%
  cpu          : usr=3.06%, sys=10.92%, ctx=533685, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=419933,628643,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=19.2MiB/s (20.2MB/s), 19.2MiB/s-19.2MiB/s (20.2MB/s-20.2MB/s), io=1640MiB (1720MB), run=85339-85339msec
  WRITE: bw=28.8MiB/s (30.2MB/s), 28.8MiB/s-28.8MiB/s (30.2MB/s-30.2MB/s), io=2456MiB (2575MB), run=85339-85339msec

Disk stats (read/write):
  vda: ios=418597/626615, merge=0/12, ticks=304180/81244, in_queue=385344, util=99.66%
```

*file-size*
```
ls -al test4K-rw-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Nov 28 09:42 test4K-rw-aio
```

## serverhand lax - 2000M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            982M     0  982M   0% /dev
tmpfs           201M  3.2M  197M   2% /run
/dev/sda1        49G  1.8G   44G   4% /
tmpfs          1001M     0 1001M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs          1001M     0 1001M   0% /sys/fs/cgroup
tmpfs           201M     0  201M   0% /run/user/901
```

*rw*
```
./fio --filename=test4K-rw-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randrw --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G --rwmixread=40
myjob: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [m(1)][1.0%][r=468KiB/s,w=632KiB/s][r=117,w=158 IOPS][eta 04m:58sJobs: 1 (f=1): [m(1)][1.3%][r=468KiB/s,w=716KiB/s][r=117,w=179 IOPS][eta 04m:57sJobs: 1 (f=1): [m(1)][1.7%][r=440KiB/s,w=736KiB/s][r=110,w=184 IOPS][eta 04m:56sJobs: 1 (f=1): [m(1)][2.0%][r=440KiB/s,w=688KiB/s][r=110,w=172 IOPS][eta 04m:55sJobs: 1 (f=1): [m(1)][2.3%][r=440KiB/s,w=680KiB/s][r=110,w=170 IOPS][eta 04m:54sJobs: 1 (f=1): [m(1)][2.7%][r=456KiB/s,w=764KiB/s][r=114,w=191 IOPS][eta 04m:53sJobs: 1 (f=1): [m(1)][3.0%][r=420KiB/s,w=632KiB/s][r=105,w=158 IOPS][eta 04m:52sJobs: 1 (f=1): [m(1)][3.3%][r=440KiB/s,w=608KiB/s][r=110,w=152 IOPS][eta 04m:51sJobs: 1 (f=1): [m(1)][3.7%][r=492KiB/s,w=672KiB/s][r=123,w=168 IOPS][eta 04m:50sJobs: 1 (f=1): [m(1)][4.0%][r=432KiB/s,w=720KiB/s][r=108,w=180 IOPS][eta 04m:49sJobs: 1 (f=1): [m(1)][4.3%][r=464KiB/s,w=572KiB/s][r=116,w=143 IOPS][eta 04m:48sJobs: 1 (f=1): [m(1)][4.7%][r=484KiB/s,w=832KiB/s][r=121,w=208 IOPS][eta 04m:47sJobs: 1 (f=1): [m(1)][5.0%][r=468KiB/s,w=708KiB/s][r=117,w=177 IOPS][eta 04m:46sJobs: 1 (f=1): [m(1)][5.3%][r=420KiB/s,w=668KiB/s][r=105,w=167 IOPS][eta 04m:45sJobs: 1 (f=1): [m(1)][5.6%][r=420KiB/s,w=656KiB/s][r=105,w=164 IOPS][eta 04m:44sJobs: 1 (f=1): [m(1)][6.0%][r=440KiB/s,w=560KiB/s][r=110,w=140 IOPS][eta 04m:43sJobs: 1 (f=1): [m(1)][6.3%][r=452KiB/s,w=748KiB/s][r=113,w=187 IOPS][eta 04m:42sJobs: 1 (f=1): [m(1)][6.6%][r=400KiB/s,w=520KiB/s][r=100,w=130 IOPS][eta 04m:41sJobs: 1 (f=1): [m(1)][7.0%][r=416KiB/s,w=796KiB/s][r=104,w=199 IOPS][eta 04m:40sJobs: 1 (f=1): [m(1)][7.3%][r=436KiB/s,w=636KiB/s][r=109,w=159 IOPS][eta 04m:39sJobs: 1 (f=1): [m(1)][7.6%][r=436KiB/s,w=540KiB/s][r=109,w=135 IOPS][eta 04m:38sJobs: 1 (f=1): [m(1)][8.0%][r=428KiB/s,w=588KiB/s][r=107,w=147 IOPS][eta 04m:37sJobs: 1 (f=1): [m(1)][8.3%][r=452KiB/s,w=676KiB/s][r=113,w=169 IOPS][eta 04m:36sJobs: 1 (f=1): [m(1)][8.6%][r=452KiB/s,w=680KiB/s][r=113,w=170 IOPS][eta 04m:35sJobs: 1 (f=1): [m(1)][9.0%][r=468KiB/s,w=524KiB/s][r=117,w=131 IOPS][eta 04m:34sJobs: 1 (f=1): [m(1)][9.3%][r=436KiB/s,w=612KiB/s][r=109,w=153 IOPS][eta 04m:33sJobs: 1 (f=1): [m(1)][9.6%][r=468KiB/s,w=632KiB/s][r=117,w=158 IOPS][eta 04m:32sJobs: 1 (f=1): [m(1)][10.0%][r=428KiB/s,w=676KiB/s][r=107,w=169 IOPS][eta 04m:31Jobs: 1 (f=1): [m(1)][10.3%][r=428KiB/s,w=652KiB/s][r=107,w=163 IOPS][eta 04m:30Jobs: 1 (f=1): [m(1)][10.6%][r=416KiB/s,w=668KiB/s][r=104,w=167 IOPS][eta 04m:29Jobs: 1 (f=1): [m(1)][11.0%][r=432KiB/s,w=708KiB/s][r=108,w=177 IOPS][eta 04m:28Jobs: 1 (f=1): [m(1)][11.3%][r=380KiB/s,w=572KiB/s][r=95,w=143 IOPS][eta 04m:27sJobs: 1 (f=1): [m(1)][11.6%][r=432KiB/s,w=624KiB/s][r=108,w=156 IOPS][eta 04m:26Jobs: 1 (f=1): [m(1)][12.0%][r=452KiB/s,w=656KiB/s][r=113,w=164 IOPS][eta 04m:25Jobs: 1 (f=1): [m(1)][12.3%][r=440KiB/s,w=600KiB/s][r=110,w=150 IOPS][eta 04m:24Jobs: 1 (f=1): [m(1)][12.6%][r=424KiB/s,w=628KiB/s][r=106,w=157 IOPS][eta 04m:23Jobs: 1 (f=1): [m(1)][13.0%][r=444KiB/s,w=616KiB/s][r=111,w=154 IOPS][eta 04m:22Jobs: 1 (f=1): [m(1)][13.3%][r=444KiB/s,w=584KiB/s][r=111,w=146 IOPS][eta 04m:21Jobs: 1 (f=1): [m(1)][13.6%][r=436KiB/s,w=656KiB/s][r=109,w=164 IOPS][eta 04m:20Jobs: 1 (f=1): [m(1)][14.0%][r=412KiB/s,w=540KiB/s][r=103,w=135 IOPS][eta 04m:19Jobs: 1 (f=1): [m(1)][14.3%][r=424KiB/s,w=712KiB/s][r=106,w=178 IOPS][eta 04m:18Jobs: 1 (f=1): [m(1)][14.6%][r=444KiB/s,w=656KiB/s][r=111,w=164 IOPS][eta 04m:17Jobs: 1 (f=1): [m(1)][15.0%][r=452KiB/s,w=548KiB/s][r=113,w=137 IOPS][eta 04m:16Jobs: 1 (f=1): [m(1)][15.3%][r=388KiB/s,w=548KiB/s][r=97,w=137 IOPS][eta 04m:15sJobs: 1 (f=1): [m(1)][15.6%][r=428KiB/s,w=476KiB/s][r=107,w=119 IOPS][eta 04m:14Jobs: 1 (f=1): [m(1)][15.9%][r=420KiB/s,w=476KiB/s][r=105,w=119 IOPS][eta 04m:13Jobs: 1 (f=1): [m(1)][16.3%][r=424KiB/s,w=540KiB/s][r=106,w=135 IOPS][eta 04m:12Jobs: 1 (f=1): [m(1)][16.6%][r=468KiB/s,w=584KiB/s][r=117,w=146 IOPS][eta 04m:11Jobs: 1 (f=1): [m(1)][16.9%][r=412KiB/s,w=516KiB/s][r=103,w=129 IOPS][eta 04m:10Jobs: 1 (f=1): [m(1)][17.3%][r=420KiB/s,w=532KiB/s][r=105,w=133 IOPS][eta 04m:09Jobs: 1 (f=1): [m(1)][17.6%][r=232KiB/s,w=328KiB/s][r=58,w=82 IOPS][eta 04m:08s]Jobs: 1 (f=1): [m(1)][17.9%][r=428KiB/s,w=724KiB/s][r=107,w=181 IOPS][eta 04m:07Jobs: 1 (f=1): [m(1)][18.3%][r=432KiB/s,w=640KiB/s][r=108,w=160 IOPS][eta 04m:06Jobs: 1 (f=1): [m(1)][18.6%][r=428KiB/s,w=632KiB/s][r=107,w=158 IOPS][eta 04m:05Jobs: 1 (f=1): [m(1)][18.9%][r=436KiB/s,w=648KiB/s][r=109,w=162 IOPS][eta 04m:04Jobs: 1 (f=1): [m(1)][19.3%][r=436KiB/s,w=584KiB/s][r=109,w=146 IOPS][eta 04m:03Jobs: 1 (f=1): [m(1)][19.6%][r=468KiB/s,w=604KiB/s][r=117,w=151 IOPS][eta 04m:02Jobs: 1 (f=1): [m(1)][19.9%][r=428KiB/s,w=576KiB/s][r=107,w=144 IOPS][eta 04m:01Jobs: 1 (f=1): [m(1)][20.3%][r=436KiB/s,w=656KiB/s][r=109,w=164 IOPS][eta 04m:00Jobs: 1 (f=1): [m(1)][20.6%][r=444KiB/s,w=724KiB/s][r=111,w=181 IOPS][eta 03m:59Jobs: 1 (f=1): [m(1)][20.9%][r=396KiB/s,w=580KiB/s][r=99,w=145 IOPS][eta 03m:58sJobs: 1 (f=1): [m(1)][21.3%][r=424KiB/s,w=680KiB/s][r=106,w=170 IOPS][eta 03m:57Jobs: 1 (f=1): [m(1)][21.6%][r=440KiB/s,w=724KiB/s][r=110,w=181 IOPS][eta 03m:56Jobs: 1 (f=1): [m(1)][21.9%][r=416KiB/s,w=684KiB/s][r=104,w=171 IOPS][eta 03m:55Jobs: 1 (f=1): [m(1)][22.3%][r=408KiB/s,w=560KiB/s][r=102,w=140 IOPS][eta 03m:54Jobs: 1 (f=1): [m(1)][22.6%][r=432KiB/s,w=648KiB/s][r=108,w=162 IOPS][eta 03m:53Jobs: 1 (f=1): [m(1)][22.9%][r=444KiB/s,w=632KiB/s][r=111,w=158 IOPS][eta 03m:52Jobs: 1 (f=1): [m(1)][23.3%][r=432KiB/s,w=628KiB/s][r=108,w=157 IOPS][eta 03m:51Jobs: 1 (f=1): [m(1)][23.6%][r=424KiB/s,w=788KiB/s][r=106,w=197 IOPS][eta 03m:50Jobs: 1 (f=1): [m(1)][23.9%][r=420KiB/s,w=652KiB/s][r=105,w=163 IOPS][eta 03m:49Jobs: 1 (f=1): [m(1)][24.3%][r=440KiB/s,w=656KiB/s][r=110,w=164 IOPS][eta 03m:48Jobs: 1 (f=1): [m(1)][24.6%][r=420KiB/s,w=724KiB/s][r=105,w=181 IOPS][eta 03m:47Jobs: 1 (f=1): [m(1)][24.9%][r=428KiB/s,w=608KiB/s][r=107,w=152 IOPS][eta 03m:46Jobs: 1 (f=1): [m(1)][25.2%][r=440KiB/s,w=512KiB/s][r=110,w=128 IOPS][eta 03m:45Jobs: 1 (f=1): [m(1)][25.6%][r=428KiB/s,w=688KiB/s][r=107,w=172 IOPS][eta 03m:44Jobs: 1 (f=1): [m(1)][25.9%][r=412KiB/s,w=552KiB/s][r=103,w=138 IOPS][eta 03m:43Jobs: 1 (f=1): [m(1)][26.2%][r=408KiB/s,w=628KiB/s][r=102,w=157 IOPS][eta 03m:42Jobs: 1 (f=1): [m(1)][26.6%][r=408KiB/s,w=660KiB/s][r=102,w=165 IOPS][eta 03m:41Jobs: 1 (f=1): [m(1)][26.9%][r=416KiB/s,w=632KiB/s][r=104,w=158 IOPS][eta 03m:40Jobs: 1 (f=1): [m(1)][27.2%][r=396KiB/s,w=572KiB/s][r=99,w=143 IOPS][eta 03m:39sJobs: 1 (f=1): [m(1)][27.6%][r=412KiB/s,w=560KiB/s][r=103,w=140 IOPS][eta 03m:38Jobs: 1 (f=1): [m(1)][27.9%][r=404KiB/s,w=604KiB/s][r=101,w=151 IOPS][eta 03m:37Jobs: 1 (f=1): [m(1)][28.2%][r=468KiB/s,w=528KiB/s][r=117,w=132 IOPS][eta 03m:36Jobs: 1 (f=1): [m(1)][28.6%][r=428KiB/s,w=708KiB/s][r=107,w=177 IOPS][eta 03m:35Jobs: 1 (f=1): [m(1)][28.9%][r=404KiB/s,w=616KiB/s][r=101,w=154 IOPS][eta 03m:34Jobs: 1 (f=1): [m(1)][29.2%][r=420KiB/s,w=604KiB/s][r=105,w=151 IOPS][eta 03m:33Jobs: 1 (f=1): [m(1)][29.6%][r=444KiB/s,w=680KiB/s][r=111,w=170 IOPS][eta 03m:32Jobs: 1 (f=1): [m(1)][29.9%][r=444KiB/s,w=668KiB/s][r=111,w=167 IOPS][eta 03m:31Jobs: 1 (f=1): [m(1)][30.2%][r=424KiB/s,w=616KiB/s][r=106,w=154 IOPS][eta 03m:30Jobs: 1 (f=1): [m(1)][30.6%][r=412KiB/s,w=600KiB/s][r=103,w=150 IOPS][eta 03m:29Jobs: 1 (f=1): [m(1)][30.9%][r=404KiB/s,w=632KiB/s][r=101,w=158 IOPS][eta 03m:28Jobs: 1 (f=1): [m(1)][31.2%][r=408KiB/s,w=624KiB/s][r=102,w=156 IOPS][eta 03m:27Jobs: 1 (f=1): [m(1)][31.6%][r=408KiB/s,w=736KiB/s][r=102,w=184 IOPS][eta 03m:26Jobs: 1 (f=1): [m(1)][31.9%][r=400KiB/s,w=636KiB/s][r=100,w=159 IOPS][eta 03m:25Jobs: 1 (f=1): [m(1)][32.2%][r=404KiB/s,w=596KiB/s][r=101,w=149 IOPS][eta 03m:24Jobs: 1 (f=1): [m(1)][32.6%][r=428KiB/s,w=644KiB/s][r=107,w=161 IOPS][eta 03m:23Jobs: 1 (f=1): [m(1)][32.9%][r=440KiB/s,w=624KiB/s][r=110,w=156 IOPS][eta 03m:22Jobs: 1 (f=1): [m(1)][33.2%][r=420KiB/s,w=824KiB/s][r=105,w=206 IOPS][eta 03m:21Jobs: 1 (f=1): [m(1)][33.6%][r=412KiB/s,w=612KiB/s][r=103,w=153 IOPS][eta 03m:20Jobs: 1 (f=1): [m(1)][33.9%][r=388KiB/s,w=688KiB/s][r=97,w=172 IOPS][eta 03m:19sJobs: 1 (f=1): [m(1)][34.2%][r=444KiB/s,w=620KiB/s][r=111,w=155 IOPS][eta 03m:18Jobs: 1 (f=1): [m(1)][34.6%][r=432KiB/s,w=616KiB/s][r=108,w=154 IOPS][eta 03m:17Jobs: 1 (f=1): [m(1)][34.9%][r=440KiB/s,w=488KiB/s][r=110,w=122 IOPS][eta 03m:16Jobs: 1 (f=1): [m(1)][35.2%][r=408KiB/s,w=528KiB/s][r=102,w=132 IOPS][eta 03m:15Jobs: 1 (f=1): [m(1)][35.5%][r=420KiB/s,w=576KiB/s][r=105,w=144 IOPS][eta 03m:14Jobs: 1 (f=1): [m(1)][35.9%][r=400KiB/s,w=696KiB/s][r=100,w=174 IOPS][eta 03m:13Jobs: 1 (f=1): [m(1)][36.2%][r=440KiB/s,w=544KiB/s][r=110,w=136 IOPS][eta 03m:12Jobs: 1 (f=1): [m(1)][36.5%][r=452KiB/s,w=672KiB/s][r=113,w=168 IOPS][eta 03m:11Jobs: 1 (f=1): [m(1)][36.9%][r=432KiB/s,w=672KiB/s][r=108,w=168 IOPS][eta 03m:10Jobs: 1 (f=1): [m(1)][37.2%][r=456KiB/s,w=640KiB/s][r=114,w=160 IOPS][eta 03m:09Jobs: 1 (f=1): [m(1)][37.5%][r=448KiB/s,w=568KiB/s][r=112,w=142 IOPS][eta 03m:08Jobs: 1 (f=1): [m(1)][37.9%][r=404KiB/s,w=556KiB/s][r=101,w=139 IOPS][eta 03m:07Jobs: 1 (f=1): [m(1)][38.2%][r=432KiB/s,w=700KiB/s][r=108,w=175 IOPS][eta 03m:06Jobs: 1 (f=1): [m(1)][38.5%][r=412KiB/s,w=696KiB/s][r=103,w=174 IOPS][eta 03m:05Jobs: 1 (f=1): [m(1)][38.9%][r=412KiB/s,w=632KiB/s][r=103,w=158 IOPS][eta 03m:04Jobs: 1 (f=1): [m(1)][39.2%][r=412KiB/s,w=628KiB/s][r=103,w=157 IOPS][eta 03m:03Jobs: 1 (f=1): [m(1)][39.5%][r=420KiB/s,w=664KiB/s][r=105,w=166 IOPS][eta 03m:02Jobs: 1 (f=1): [m(1)][39.9%][r=432KiB/s,w=500KiB/s][r=108,w=125 IOPS][eta 03m:01Jobs: 1 (f=1): [m(1)][40.2%][r=436KiB/s,w=564KiB/s][r=109,w=141 IOPS][eta 03m:00Jobs: 1 (f=1): [m(1)][40.5%][r=416KiB/s,w=636KiB/s][r=104,w=159 IOPS][eta 02m:59Jobs: 1 (f=1): [m(1)][40.9%][r=440KiB/s,w=584KiB/s][r=110,w=146 IOPS][eta 02m:58Jobs: 1 (f=1): [m(1)][41.2%][r=396KiB/s,w=836KiB/s][r=99,w=209 IOPS][eta 02m:57sJobs: 1 (f=1): [m(1)][41.5%][r=392KiB/s,w=628KiB/s][r=98,w=157 IOPS][eta 02m:56sJobs: 1 (f=1): [m(1)][41.9%][r=444KiB/s,w=612KiB/s][r=111,w=153 IOPS][eta 02m:55Jobs: 1 (f=1): [m(1)][42.2%][r=464KiB/s,w=424KiB/s][r=116,w=106 IOPS][eta 02m:54Jobs: 1 (f=1): [m(1)][42.5%][r=432KiB/s,w=568KiB/s][r=108,w=142 IOPS][eta 02m:53Jobs: 1 (f=1): [m(1)][42.9%][r=400KiB/s,w=612KiB/s][r=100,w=153 IOPS][eta 02m:52Jobs: 1 (f=1): [m(1)][43.2%][r=408KiB/s,w=568KiB/s][r=102,w=142 IOPS][eta 02m:51Jobs: 1 (f=1): [m(1)][43.5%][r=412KiB/s,w=852KiB/s][r=103,w=213 IOPS][eta 02m:50Jobs: 1 (f=1): [m(1)][43.9%][r=396KiB/s,w=544KiB/s][r=99,w=136 IOPS][eta 02m:49sJobs: 1 (f=1): [m(1)][44.2%][r=396KiB/s,w=692KiB/s][r=99,w=173 IOPS][eta 02m:48sJobs: 1 (f=1): [m(1)][44.5%][r=388KiB/s,w=476KiB/s][r=97,w=119 IOPS][eta 02m:47sJobs: 1 (f=1): [m(1)][44.9%][r=424KiB/s,w=496KiB/s][r=106,w=124 IOPS][eta 02m:46Jobs: 1 (f=1): [m(1)][45.2%][r=424KiB/s,w=520KiB/s][r=106,w=130 IOPS][eta 02m:45Jobs: 1 (f=1): [m(1)][45.5%][r=432KiB/s,w=588KiB/s][r=108,w=147 IOPS][eta 02m:44Jobs: 1 (f=1): [m(1)][45.8%][r=412KiB/s,w=684KiB/s][r=103,w=171 IOPS][eta 02m:43Jobs: 1 (f=1): [m(1)][46.2%][r=424KiB/s,w=692KiB/s][r=106,w=173 IOPS][eta 02m:42Jobs: 1 (f=1): [m(1)][46.5%][r=444KiB/s,w=528KiB/s][r=111,w=132 IOPS][eta 02m:41Jobs: 1 (f=1): [m(1)][46.8%][r=404KiB/s,w=492KiB/s][r=101,w=123 IOPS][eta 02m:40Jobs: 1 (f=1): [m(1)][47.2%][r=408KiB/s,w=596KiB/s][r=102,w=149 IOPS][eta 02m:39Jobs: 1 (f=1): [m(1)][47.5%][r=388KiB/s,w=692KiB/s][r=97,w=173 IOPS][eta 02m:38sJobs: 1 (f=1): [m(1)][47.8%][r=436KiB/s,w=552KiB/s][r=109,w=138 IOPS][eta 02m:37Jobs: 1 (f=1): [m(1)][48.2%][r=420KiB/s,w=688KiB/s][r=105,w=172 IOPS][eta 02m:36Jobs: 1 (f=1): [m(1)][48.5%][r=416KiB/s,w=552KiB/s][r=104,w=138 IOPS][eta 02m:35Jobs: 1 (f=1): [m(1)][48.8%][r=412KiB/s,w=624KiB/s][r=103,w=156 IOPS][eta 02m:34Jobs: 1 (f=1): [m(1)][49.2%][r=420KiB/s,w=616KiB/s][r=105,w=154 IOPS][eta 02m:33Jobs: 1 (f=1): [m(1)][49.5%][r=400KiB/s,w=584KiB/s][r=100,w=146 IOPS][eta 02m:32Jobs: 1 (f=1): [m(1)][49.8%][r=432KiB/s,w=584KiB/s][r=108,w=146 IOPS][eta 02m:31Jobs: 1 (f=1): [m(1)][50.2%][r=420KiB/s,w=616KiB/s][r=105,w=154 IOPS][eta 02m:30Jobs: 1 (f=1): [m(1)][50.5%][r=392KiB/s,w=628KiB/s][r=98,w=157 IOPS][eta 02m:29sJobs: 1 (f=1): [m(1)][50.8%][r=300KiB/s,w=492KiB/s][r=75,w=123 IOPS][eta 02m:28sJobs: 1 (f=1): [m(1)][51.2%][r=380KiB/s,w=516KiB/s][r=95,w=129 IOPS][eta 02m:27sJobs: 1 (f=1): [m(1)][51.5%][r=376KiB/s,w=504KiB/s][r=94,w=126 IOPS][eta 02m:26sJobs: 1 (f=1): [m(1)][51.8%][r=408KiB/s,w=508KiB/s][r=102,w=127 IOPS][eta 02m:25Jobs: 1 (f=1): [m(1)][52.2%][r=420KiB/s,w=792KiB/s][r=105,w=198 IOPS][eta 02m:24Jobs: 1 (f=1): [m(1)][52.5%][r=388KiB/s,w=636KiB/s][r=97,w=159 IOPS][eta 02m:23sJobs: 1 (f=1): [m(1)][52.8%][r=416KiB/s,w=664KiB/s][r=104,w=166 IOPS][eta 02m:22Jobs: 1 (f=1): [m(1)][53.2%][r=416KiB/s,w=608KiB/s][r=104,w=152 IOPS][eta 02m:21Jobs: 1 (f=1): [m(1)][53.5%][r=448KiB/s,w=548KiB/s][r=112,w=137 IOPS][eta 02m:20Jobs: 1 (f=1): [m(1)][53.8%][r=400KiB/s,w=612KiB/s][r=100,w=153 IOPS][eta 02m:19Jobs: 1 (f=1): [m(1)][54.2%][r=448KiB/s,w=556KiB/s][r=112,w=139 IOPS][eta 02m:18Jobs: 1 (f=1): [m(1)][54.5%][r=424KiB/s,w=572KiB/s][r=106,w=143 IOPS][eta 02m:17Jobs: 1 (f=1): [m(1)][54.8%][r=400KiB/s,w=656KiB/s][r=100,w=164 IOPS][eta 02m:16Jobs: 1 (f=1): [m(1)][55.1%][r=396KiB/s,w=844KiB/s][r=99,w=211 IOPS][eta 02m:15sJobs: 1 (f=1): [m(1)][55.5%][r=412KiB/s,w=764KiB/s][r=103,w=191 IOPS][eta 02m:14Jobs: 1 (f=1): [m(1)][55.8%][r=412KiB/s,w=556KiB/s][r=103,w=139 IOPS][eta 02m:13Jobs: 1 (f=1): [m(1)][56.1%][r=416KiB/s,w=600KiB/s][r=104,w=150 IOPS][eta 02m:12Jobs: 1 (f=1): [m(1)][56.5%][r=428KiB/s,w=536KiB/s][r=107,w=134 IOPS][eta 02m:11Jobs: 1 (f=1): [m(1)][56.8%][r=436KiB/s,w=784KiB/s][r=109,w=196 IOPS][eta 02m:10Jobs: 1 (f=1): [m(1)][57.1%][r=424KiB/s,w=640KiB/s][r=106,w=160 IOPS][eta 02m:09Jobs: 1 (f=1): [m(1)][57.5%][r=416KiB/s,w=552KiB/s][r=104,w=138 IOPS][eta 02m:08Jobs: 1 (f=1): [m(1)][57.8%][r=392KiB/s,w=644KiB/s][r=98,w=161 IOPS][eta 02m:07sJobs: 1 (f=1): [m(1)][58.1%][r=424KiB/s,w=700KiB/s][r=106,w=175 IOPS][eta 02m:06Jobs: 1 (f=1): [m(1)][58.5%][r=420KiB/s,w=664KiB/s][r=105,w=166 IOPS][eta 02m:05Jobs: 1 (f=1): [m(1)][58.8%][r=444KiB/s,w=512KiB/s][r=111,w=128 IOPS][eta 02m:04Jobs: 1 (f=1): [m(1)][59.1%][r=428KiB/s,w=672KiB/s][r=107,w=168 IOPS][eta 02m:03Jobs: 1 (f=1): [m(1)][59.5%][r=428KiB/s,w=708KiB/s][r=107,w=177 IOPS][eta 02m:02Jobs: 1 (f=1): [m(1)][59.8%][r=444KiB/s,w=560KiB/s][r=111,w=140 IOPS][eta 02m:01Jobs: 1 (f=1): [m(1)][60.1%][r=412KiB/s,w=668KiB/s][r=103,w=167 IOPS][eta 02m:00Jobs: 1 (f=1): [m(1)][60.5%][r=388KiB/s,w=760KiB/s][r=97,w=190 IOPS][eta 01m:59sJobs: 1 (f=1): [m(1)][60.8%][r=424KiB/s,w=568KiB/s][r=106,w=142 IOPS][eta 01m:58Jobs: 1 (f=1): [m(1)][61.1%][r=400KiB/s,w=668KiB/s][r=100,w=167 IOPS][eta 01m:57Jobs: 1 (f=1): [m(1)][61.5%][r=460KiB/s,w=484KiB/s][r=115,w=121 IOPS][eta 01m:56Jobs: 1 (f=1): [m(1)][61.8%][r=428KiB/s,w=508KiB/s][r=107,w=127 IOPS][eta 01m:55Jobs: 1 (f=1): [m(1)][62.1%][r=444KiB/s,w=628KiB/s][r=111,w=157 IOPS][eta 01m:54Jobs: 1 (f=1): [m(1)][62.5%][r=412KiB/s,w=668KiB/s][r=103,w=167 IOPS][eta 01m:53Jobs: 1 (f=1): [m(1)][62.8%][r=420KiB/s,w=672KiB/s][r=105,w=168 IOPS][eta 01m:52Jobs: 1 (f=1): [m(1)][63.1%][r=444KiB/s,w=520KiB/s][r=111,w=130 IOPS][eta 01m:51Jobs: 1 (f=1): [m(1)][63.5%][r=396KiB/s,w=640KiB/s][r=99,w=160 IOPS][eta 01m:50sJobs: 1 (f=1): [m(1)][63.8%][r=416KiB/s,w=640KiB/s][r=104,w=160 IOPS][eta 01m:49Jobs: 1 (f=1): [m(1)][64.1%][r=420KiB/s,w=768KiB/s][r=105,w=192 IOPS][eta 01m:48Jobs: 1 (f=1): [m(1)][64.5%][r=452KiB/s,w=500KiB/s][r=113,w=125 IOPS][eta 01m:47Jobs: 1 (f=1): [m(1)][64.8%][r=384KiB/s,w=660KiB/s][r=96,w=165 IOPS][eta 01m:46sJobs: 1 (f=1): [m(1)][65.1%][r=464KiB/s,w=640KiB/s][r=116,w=160 IOPS][eta 01m:45Jobs: 1 (f=1): [m(1)][65.4%][r=456KiB/s,w=644KiB/s][r=114,w=161 IOPS][eta 01m:44Jobs: 1 (f=1): [m(1)][65.8%][r=428KiB/s,w=644KiB/s][r=107,w=161 IOPS][eta 01m:43Jobs: 1 (f=1): [m(1)][66.1%][r=424KiB/s,w=640KiB/s][r=106,w=160 IOPS][eta 01m:42Jobs: 1 (f=1): [m(1)][66.4%][r=428KiB/s,w=752KiB/s][r=107,w=188 IOPS][eta 01m:41Jobs: 1 (f=1): [m(1)][66.8%][r=424KiB/s,w=720KiB/s][r=106,w=180 IOPS][eta 01m:40Jobs: 1 (f=1): [m(1)][67.1%][r=408KiB/s,w=588KiB/s][r=102,w=147 IOPS][eta 01m:39Jobs: 1 (f=1): [m(1)][67.4%][r=428KiB/s,w=528KiB/s][r=107,w=132 IOPS][eta 01m:38Jobs: 1 (f=1): [m(1)][67.8%][r=412KiB/s,w=592KiB/s][r=103,w=148 IOPS][eta 01m:37Jobs: 1 (f=1): [m(1)][68.1%][r=408KiB/s,w=732KiB/s][r=102,w=183 IOPS][eta 01m:36Jobs: 1 (f=1): [m(1)][68.4%][r=404KiB/s,w=592KiB/s][r=101,w=148 IOPS][eta 01m:35Jobs: 1 (f=1): [m(1)][68.8%][r=412KiB/s,w=484KiB/s][r=103,w=121 IOPS][eta 01m:34Jobs: 1 (f=1): [m(1)][69.1%][r=444KiB/s,w=688KiB/s][r=111,w=172 IOPS][eta 01m:33Jobs: 1 (f=1): [m(1)][69.4%][r=440KiB/s,w=636KiB/s][r=110,w=159 IOPS][eta 01m:32Jobs: 1 (f=1): [m(1)][69.8%][r=416KiB/s,w=552KiB/s][r=104,w=138 IOPS][eta 01m:31Jobs: 1 (f=1): [m(1)][70.1%][r=404KiB/s,w=572KiB/s][r=101,w=143 IOPS][eta 01m:30Jobs: 1 (f=1): [m(1)][70.4%][r=424KiB/s,w=584KiB/s][r=106,w=146 IOPS][eta 01m:29Jobs: 1 (f=1): [m(1)][70.8%][r=396KiB/s,w=620KiB/s][r=99,w=155 IOPS][eta 01m:28sJobs: 1 (f=1): [m(1)][71.1%][r=416KiB/s,w=508KiB/s][r=104,w=127 IOPS][eta 01m:27Jobs: 1 (f=1): [m(1)][71.4%][r=408KiB/s,w=508KiB/s][r=102,w=127 IOPS][eta 01m:26Jobs: 1 (f=1): [m(1)][71.8%][r=396KiB/s,w=748KiB/s][r=99,w=187 IOPS][eta 01m:25sJobs: 1 (f=1): [m(1)][72.1%][r=404KiB/s,w=664KiB/s][r=101,w=166 IOPS][eta 01m:24Jobs: 1 (f=1): [m(1)][72.4%][r=404KiB/s,w=544KiB/s][r=101,w=136 IOPS][eta 01m:23Jobs: 1 (f=1): [m(1)][72.8%][r=428KiB/s,w=532KiB/s][r=107,w=133 IOPS][eta 01m:22Jobs: 1 (f=1): [m(1)][73.1%][r=400KiB/s,w=676KiB/s][r=100,w=169 IOPS][eta 01m:21Jobs: 1 (f=1): [m(1)][73.4%][r=400KiB/s,w=664KiB/s][r=100,w=166 IOPS][eta 01m:20Jobs: 1 (f=1): [m(1)][73.8%][r=448KiB/s,w=500KiB/s][r=112,w=125 IOPS][eta 01m:19Jobs: 1 (f=1): [m(1)][74.1%][r=400KiB/s,w=804KiB/s][r=100,w=201 IOPS][eta 01m:18Jobs: 1 (f=1): [m(1)][74.4%][r=400KiB/s,w=664KiB/s][r=100,w=166 IOPS][eta 01m:17Jobs: 1 (f=1): [m(1)][74.8%][r=404KiB/s,w=612KiB/s][r=101,w=153 IOPS][eta 01m:16Jobs: 1 (f=1): [m(1)][75.1%][r=400KiB/s,w=676KiB/s][r=100,w=169 IOPS][eta 01m:15Jobs: 1 (f=1): [m(1)][75.4%][r=444KiB/s,w=600KiB/s][r=111,w=150 IOPS][eta 01m:14Jobs: 1 (f=1): [m(1)][75.7%][r=444KiB/s,w=692KiB/s][r=111,w=173 IOPS][eta 01m:13Jobs: 1 (f=1): [m(1)][76.1%][r=400KiB/s,w=632KiB/s][r=100,w=158 IOPS][eta 01m:12Jobs: 1 (f=1): [m(1)][76.4%][r=424KiB/s,w=548KiB/s][r=106,w=137 IOPS][eta 01m:11Jobs: 1 (f=1): [m(1)][76.7%][r=408KiB/s,w=620KiB/s][r=102,w=155 IOPS][eta 01m:10Jobs: 1 (f=1): [m(1)][77.1%][r=428KiB/s,w=552KiB/s][r=107,w=138 IOPS][eta 01m:09Jobs: 1 (f=1): [m(1)][77.4%][r=408KiB/s,w=676KiB/s][r=102,w=169 IOPS][eta 01m:08Jobs: 1 (f=1): [m(1)][77.7%][r=444KiB/s,w=600KiB/s][r=111,w=150 IOPS][eta 01m:07Jobs: 1 (f=1): [m(1)][78.1%][r=396KiB/s,w=708KiB/s][r=99,w=177 IOPS][eta 01m:06sJobs: 1 (f=1): [m(1)][78.4%][r=412KiB/s,w=540KiB/s][r=103,w=135 IOPS][eta 01m:05Jobs: 1 (f=1): [m(1)][78.7%][r=364KiB/s,w=620KiB/s][r=91,w=155 IOPS][eta 01m:04sJobs: 1 (f=1): [m(1)][79.1%][r=388KiB/s,w=628KiB/s][r=97,w=157 IOPS][eta 01m:03sJobs: 1 (f=1): [m(1)][79.4%][r=420KiB/s,w=596KiB/s][r=105,w=149 IOPS][eta 01m:02Jobs: 1 (f=1): [m(1)][79.7%][r=392KiB/s,w=740KiB/s][r=98,w=185 IOPS][eta 01m:01sJobs: 1 (f=1): [m(1)][80.1%][r=432KiB/s,w=592KiB/s][r=108,w=148 IOPS][eta 01m:00Jobs: 1 (f=1): [m(1)][80.4%][r=420KiB/s,w=676KiB/s][r=105,w=169 IOPS][eta 00m:59Jobs: 1 (f=1): [m(1)][80.7%][r=424KiB/s,w=596KiB/s][r=106,w=149 IOPS][eta 00m:58Jobs: 1 (f=1): [m(1)][81.1%][r=416KiB/s,w=708KiB/s][r=104,w=177 IOPS][eta 00m:57Jobs: 1 (f=1): [m(1)][81.4%][r=416KiB/s,w=588KiB/s][r=104,w=147 IOPS][eta 00m:56Jobs: 1 (f=1): [m(1)][81.7%][r=444KiB/s,w=680KiB/s][r=111,w=170 IOPS][eta 00m:55Jobs: 1 (f=1): [m(1)][82.1%][r=396KiB/s,w=716KiB/s][r=99,w=179 IOPS][eta 00m:54sJobs: 1 (f=1): [m(1)][82.4%][r=428KiB/s,w=656KiB/s][r=107,w=164 IOPS][eta 00m:53Jobs: 1 (f=1): [m(1)][82.7%][r=412KiB/s,w=580KiB/s][r=103,w=145 IOPS][eta 00m:52Jobs: 1 (f=1): [m(1)][83.1%][r=392KiB/s,w=616KiB/s][r=98,w=154 IOPS][eta 00m:51sJobs: 1 (f=1): [m(1)][83.4%][r=404KiB/s,w=624KiB/s][r=101,w=156 IOPS][eta 00m:50Jobs: 1 (f=1): [m(1)][83.7%][r=412KiB/s,w=632KiB/s][r=103,w=158 IOPS][eta 00m:49Jobs: 1 (f=1): [m(1)][84.1%][r=416KiB/s,w=616KiB/s][r=104,w=154 IOPS][eta 00m:48Jobs: 1 (f=1): [m(1)][84.4%][r=420KiB/s,w=612KiB/s][r=105,w=153 IOPS][eta 00m:47Jobs: 1 (f=1): [m(1)][84.7%][r=432KiB/s,w=652KiB/s][r=108,w=163 IOPS][eta 00m:46Jobs: 1 (f=1): [m(1)][85.0%][r=444KiB/s,w=664KiB/s][r=111,w=166 IOPS][eta 00m:45Jobs: 1 (f=1): [m(1)][85.4%][r=408KiB/s,w=644KiB/s][r=102,w=161 IOPS][eta 00m:44Jobs: 1 (f=1): [m(1)][85.7%][r=428KiB/s,w=584KiB/s][r=107,w=146 IOPS][eta 00m:43Jobs: 1 (f=1): [m(1)][86.0%][r=400KiB/s,w=700KiB/s][r=100,w=175 IOPS][eta 00m:42Jobs: 1 (f=1): [m(1)][86.4%][r=392KiB/s,w=836KiB/s][r=98,w=209 IOPS][eta 00m:41sJobs: 1 (f=1): [m(1)][86.7%][r=392KiB/s,w=620KiB/s][r=98,w=155 IOPS][eta 00m:40sJobs: 1 (f=1): [m(1)][87.0%][r=380KiB/s,w=676KiB/s][r=95,w=169 IOPS][eta 00m:39sJobs: 1 (f=1): [m(1)][87.4%][r=392KiB/s,w=516KiB/s][r=98,w=129 IOPS][eta 00m:38sJobs: 1 (f=1): [m(1)][87.7%][r=420KiB/s,w=644KiB/s][r=105,w=161 IOPS][eta 00m:37Jobs: 1 (f=1): [m(1)][88.0%][r=420KiB/s,w=576KiB/s][r=105,w=144 IOPS][eta 00m:36Jobs: 1 (f=1): [m(1)][88.4%][r=400KiB/s,w=648KiB/s][r=100,w=162 IOPS][eta 00m:35Jobs: 1 (f=1): [m(1)][88.7%][r=396KiB/s,w=716KiB/s][r=99,w=179 IOPS][eta 00m:34sJobs: 1 (f=1): [m(1)][89.0%][r=384KiB/s,w=616KiB/s][r=96,w=154 IOPS][eta 00m:33sJobs: 1 (f=1): [m(1)][89.4%][r=412KiB/s,w=484KiB/s][r=103,w=121 IOPS][eta 00m:32Jobs: 1 (f=1): [m(1)][89.7%][r=416KiB/s,w=744KiB/s][r=104,w=186 IOPS][eta 00m:31Jobs: 1 (f=1): [m(1)][90.0%][r=420KiB/s,w=716KiB/s][r=105,w=179 IOPS][eta 00m:30Jobs: 1 (f=1): [m(1)][90.4%][r=408KiB/s,w=652KiB/s][r=102,w=163 IOPS][eta 00m:29Jobs: 1 (f=1): [m(1)][90.7%][r=424KiB/s,w=612KiB/s][r=106,w=153 IOPS][eta 00m:28Jobs: 1 (f=1): [m(1)][91.0%][r=432KiB/s,w=624KiB/s][r=108,w=156 IOPS][eta 00m:27Jobs: 1 (f=1): [m(1)][91.4%][r=400KiB/s,w=568KiB/s][r=100,w=142 IOPS][eta 00m:26Jobs: 1 (f=1): [m(1)][91.7%][r=428KiB/s,w=612KiB/s][r=107,w=153 IOPS][eta 00m:25Jobs: 1 (f=1): [m(1)][92.0%][r=408KiB/s,w=696KiB/s][r=102,w=174 IOPS][eta 00m:24Jobs: 1 (f=1): [m(1)][92.4%][r=424KiB/s,w=580KiB/s][r=106,w=145 IOPS][eta 00m:23Jobs: 1 (f=1): [m(1)][92.7%][r=420KiB/s,w=504KiB/s][r=105,w=126 IOPS][eta 00m:22Jobs: 1 (f=1): [m(1)][93.0%][r=420KiB/s,w=532KiB/s][r=105,w=133 IOPS][eta 00m:21Jobs: 1 (f=1): [m(1)][93.4%][r=408KiB/s,w=556KiB/s][r=102,w=139 IOPS][eta 00m:20Jobs: 1 (f=1): [m(1)][93.7%][r=428KiB/s,w=592KiB/s][r=107,w=148 IOPS][eta 00m:19Jobs: 1 (f=1): [m(1)][94.0%][r=420KiB/s,w=660KiB/s][r=105,w=165 IOPS][eta 00m:18Jobs: 1 (f=1): [m(1)][94.4%][r=420KiB/s,w=600KiB/s][r=105,w=150 IOPS][eta 00m:17Jobs: 1 (f=1): [m(1)][94.7%][r=416KiB/s,w=640KiB/s][r=104,w=160 IOPS][eta 00m:16Jobs: 1 (f=1): [m(1)][95.0%][r=400KiB/s,w=644KiB/s][r=100,w=161 IOPS][eta 00m:15Jobs: 1 (f=1): [m(1)][95.3%][r=400KiB/s,w=468KiB/s][r=100,w=117 IOPS][eta 00m:14Jobs: 1 (f=1): [m(1)][95.7%][r=412KiB/s,w=712KiB/s][r=103,w=178 IOPS][eta 00m:13Jobs: 1 (f=1): [m(1)][96.0%][r=400KiB/s,w=628KiB/s][r=100,w=157 IOPS][eta 00m:12Jobs: 1 (f=1): [m(1)][96.3%][r=436KiB/s,w=668KiB/s][r=109,w=167 IOPS][eta 00m:11Jobs: 1 (f=1): [m(1)][96.7%][r=400KiB/s,w=656KiB/s][r=100,w=164 IOPS][eta 00m:10Jobs: 1 (f=1): [m(1)][97.0%][r=412KiB/s,w=652KiB/s][r=103,w=163 IOPS][eta 00m:09Jobs: 1 (f=1): [m(1)][97.3%][r=420KiB/s,w=700KiB/s][r=105,w=175 IOPS][eta 00m:08Jobs: 1 (f=1): [m(1)][97.7%][r=424KiB/s,w=676KiB/s][r=106,w=169 IOPS][eta 00m:07Jobs: 1 (f=1): [m(1)][98.0%][r=408KiB/s,w=664KiB/s][r=102,w=166 IOPS][eta 00m:06Jobs: 1 (f=1): [m(1)][98.3%][r=436KiB/s,w=680KiB/s][r=109,w=170 IOPS][eta 00m:05Jobs: 1 (f=1): [m(1)][98.7%][r=436KiB/s,w=584KiB/s][r=109,w=146 IOPS][eta 00m:04Jobs: 1 (f=1): [m(1)][99.0%][r=428KiB/s,w=548KiB/s][r=107,w=137 IOPS][eta 00m:03Jobs: 1 (f=1): [m(1)][99.3%][r=428KiB/s,w=564KiB/s][r=107,w=141 IOPS][eta 00m:02Jobs: 1 (f=1): [m(1)][99.7%][r=424KiB/s,w=636KiB/s][r=106,w=159 IOPS][eta 00m:01Jobs: 1 (f=1): [m(1)][100.0%][r=432KiB/s,w=536KiB/s][r=108,w=134 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16669: Wed Nov 29 14:37:11 2017
   read: IOPS=105, BW=421KiB/s (431kB/s)(123MiB/300022msec)
    slat (usec): min=2, max=33277, avg=29.17, stdev=483.19
    clat (usec): min=34, max=510866, avg=18311.55, stdev=8907.89
     lat (usec): min=1053, max=510887, avg=18341.39, stdev=8895.67
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    7], 10.00th=[    9], 20.00th=[   12],
     | 30.00th=[   14], 40.00th=[   16], 50.00th=[   18], 60.00th=[   20],
     | 70.00th=[   22], 80.00th=[   26], 90.00th=[   30], 95.00th=[   33],
     | 99.00th=[   41], 99.50th=[   43], 99.90th=[   49], 99.95th=[   53],
     | 99.99th=[  224]
   bw (  KiB/s): min=  176, max=  544, per=100.00%, avg=420.59, stdev=30.40, samples=600
   iops        : min=   44, max=  136, avg=105.10, stdev= 7.62, samples=600
  write: IOPS=156, BW=625KiB/s (640kB/s)(183MiB/300022msec)
    slat (usec): min=2, max=32151, avg=25.59, stdev=335.09
    clat (usec): min=493, max=519429, avg=13219.91, stdev=9687.04
     lat (usec): min=637, max=519451, avg=13246.19, stdev=9692.25
    clat percentiles (usec):
     |  1.00th=[ 1958],  5.00th=[ 2147], 10.00th=[ 2311], 20.00th=[ 2671],
     | 30.00th=[ 7439], 40.00th=[ 9896], 50.00th=[11994], 60.00th=[14091],
     | 70.00th=[17171], 80.00th=[20841], 90.00th=[25822], 95.00th=[30540],
     | 99.00th=[40109], 99.50th=[43254], 99.90th=[50594], 99.95th=[54264],
     | 99.99th=[67634]
   bw (  KiB/s): min=  264, max=  936, per=99.99%, avg=624.91, stdev=109.49, samples=600
   iops        : min=   66, max=  234, avg=156.19, stdev=27.38, samples=600
  lat (usec)   : 50=0.02%, 100=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=1.13%, 4=13.01%, 10=16.43%, 20=40.73%, 50=28.57%
  lat (msec)   : 100=0.09%, 250=0.01%, 500=0.01%, 750=0.01%
  cpu          : usr=1.51%, sys=3.89%, ctx=78666, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=31551,46879,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=421KiB/s (431kB/s), 421KiB/s-421KiB/s (431kB/s-431kB/s), io=123MiB (129MB), run=300022-300022msec
  WRITE: bw=625KiB/s (640kB/s), 625KiB/s-625KiB/s (640kB/s-640kB/s), io=183MiB (192MB), run=300022-300022msec

Disk stats (read/write):
  sda: ios=31619/46989, merge=299/62, ticks=571988/609892, in_queue=1181820, util=100.00%
```

*file-size*
```
ls -al test4K-rw-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Nov 29 14:37 test4K-rw-aio
```

## hiformance lax - 2000M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            981M     0  981M   0% /dev
tmpfs           201M  5.8M  195M   3% /run
/dev/vda1        33G  2.5G   30G   8% /
tmpfs          1001M     0 1001M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs          1001M     0 1001M   0% /sys/fs/cgroup
tmpfs           201M     0  201M   0% /run/user/901
```

*rw*
```
./fio --filename=test4K-rw-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randrw --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G --rwmixread=40
myjob: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [m(1)][4.3%][r=26.0MiB/s,w=38.1MiB/s][r=6667,w=9762 IOPS][eta 01mJobs: 1 (f=1): [m(1)][5.8%][r=24.1MiB/s,w=36.3MiB/s][r=6182,w=9300 IOPS][eta 01mJobs: 1 (f=1): [m(1)][7.4%][r=24.2MiB/s,w=37.6MiB/s][r=6189,w=9628 IOPS][eta 01mJobs: 1 (f=1): [m(1)][9.0%][r=26.3MiB/s,w=38.8MiB/s][r=6742,w=9921 IOPS][eta 01mJobs: 1 (f=1): [m(1)][10.6%][r=27.5MiB/s,w=41.6MiB/s][r=7039,w=10.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][12.3%][r=28.3MiB/s,w=42.7MiB/s][r=7251,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][14.1%][r=28.1MiB/s,w=41.2MiB/s][r=7181,w=10.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][15.9%][r=28.6MiB/s,w=42.7MiB/s][r=7314,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][17.5%][r=28.2MiB/s,w=41.7MiB/s][r=7212,w=10.7k IOPS][eta 0Jobs: 1 (f=1): [m(1)][19.4%][r=27.8MiB/s,w=42.3MiB/s][r=7128,w=10.8k IOPS][eta 0Jobs: 1 (f=1): [m(1)][21.0%][r=29.2MiB/s,w=44.0MiB/s][r=7469,w=11.3k IOPS][eta 0Jobs: 1 (f=1): [m(1)][22.6%][r=28.6MiB/s,w=43.1MiB/s][r=7329,w=11.0k IOPS][eta 0Jobs: 1 (f=1): [m(1)][24.2%][r=26.7MiB/s,w=40.0MiB/s][r=6834,w=10.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][25.8%][r=26.8MiB/s,w=39.9MiB/s][r=6850,w=10.2k IOPS][eta 0Jobs: 1 (f=1): [m(1)][27.4%][r=27.2MiB/s,w=40.9MiB/s][r=6955,w=10.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][29.5%][r=27.5MiB/s,w=41.1MiB/s][r=7039,w=10.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][31.1%][r=28.3MiB/s,w=42.6MiB/s][r=7237,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][32.8%][r=28.4MiB/s,w=43.5MiB/s][r=7279,w=11.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][34.4%][r=27.4MiB/s,w=42.4MiB/s][r=7008,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][34.9%][r=28.7MiB/s,w=42.6MiB/s][r=7353,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][37.7%][r=27.9MiB/s,w=42.9MiB/s][r=7147,w=10.0k IOPS][eta 0Jobs: 1 (f=1): [m(1)][39.3%][r=27.1MiB/s,w=41.4MiB/s][r=6926,w=10.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][41.0%][r=28.2MiB/s,w=42.7MiB/s][r=7232,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][42.6%][r=26.5MiB/s,w=40.7MiB/s][r=6791,w=10.4k IOPS][eta 0Jobs: 1 (f=1): [m(1)][44.3%][r=28.1MiB/s,w=42.3MiB/s][r=7200,w=10.8k IOPS][eta 0Jobs: 1 (f=1): [m(1)][46.7%][r=28.0MiB/s,w=43.1MiB/s][r=7416,w=11.0k IOPS][eta 0Jobs: 1 (f=1): [m(1)][48.3%][r=27.0MiB/s,w=42.2MiB/s][r=7166,w=10.8k IOPS][eta 0Jobs: 1 (f=1): [m(1)][50.0%][r=27.9MiB/s,w=41.9MiB/s][r=7154,w=10.7k IOPS][eta 0Jobs: 1 (f=1): [m(1)][51.7%][r=28.4MiB/s,w=41.5MiB/s][r=7259,w=10.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][53.3%][r=28.6MiB/s,w=42.6MiB/s][r=7334,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][55.0%][r=28.2MiB/s,w=41.9MiB/s][r=7227,w=10.7k IOPS][eta 0Jobs: 1 (f=1): [m(1)][56.7%][r=29.4MiB/s,w=43.7MiB/s][r=7527,w=11.2k IOPS][eta 0Jobs: 1 (f=1): [m(1)][58.3%][r=29.6MiB/s,w=42.7MiB/s][r=7575,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][60.0%][r=28.5MiB/s,w=42.9MiB/s][r=7285,w=10.0k IOPS][eta 0Jobs: 1 (f=1): [m(1)][61.7%][r=28.0MiB/s,w=42.4MiB/s][r=7411,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][63.3%][r=29.0MiB/s,w=44.7MiB/s][r=7679,w=11.4k IOPS][eta 0Jobs: 1 (f=1): [m(1)][65.0%][r=29.5MiB/s,w=44.4MiB/s][r=7563,w=11.4k IOPS][eta 0Jobs: 1 (f=1): [m(1)][66.7%][r=27.5MiB/s,w=40.7MiB/s][r=7033,w=10.4k IOPS][eta 0Jobs: 1 (f=1): [m(1)][68.3%][r=27.4MiB/s,w=40.9MiB/s][r=7008,w=10.5k IOPS][eta 0Jobs: 1 (f=1): [m(1)][70.0%][r=27.5MiB/s,w=42.5MiB/s][r=7034,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][71.7%][r=28.9MiB/s,w=42.2MiB/s][r=7390,w=10.8k IOPS][eta 0Jobs: 1 (f=1): [m(1)][73.3%][r=28.9MiB/s,w=43.4MiB/s][r=7409,w=11.1k IOPS][eta 0Jobs: 1 (f=1): [m(1)][75.0%][r=28.2MiB/s,w=42.5MiB/s][r=7229,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][78.0%][r=28.0MiB/s,w=42.1MiB/s][r=7172,w=10.8k IOPS][eta 0Jobs: 1 (f=1): [m(1)][79.7%][r=28.1MiB/s,w=42.5MiB/s][r=7189,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][81.4%][r=28.9MiB/s,w=42.6MiB/s][r=7402,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][83.1%][r=28.0MiB/s,w=42.9MiB/s][r=7170,w=10.0k IOPS][eta 0Jobs: 1 (f=1): [m(1)][84.7%][r=29.0MiB/s,w=44.1MiB/s][r=7434,w=11.3k IOPS][eta 0Jobs: 1 (f=1): [m(1)][86.4%][r=28.8MiB/s,w=42.5MiB/s][r=7360,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][88.1%][r=28.1MiB/s,w=41.8MiB/s][r=7182,w=10.7k IOPS][eta 0Jobs: 1 (f=1): [m(1)][89.8%][r=28.3MiB/s,w=42.8MiB/s][r=7256,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][91.5%][r=28.7MiB/s,w=42.8MiB/s][r=7350,w=10.9k IOPS][eta 0Jobs: 1 (f=1): [m(1)][93.2%][r=28.2MiB/s,w=41.5MiB/s][r=7218,w=10.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][94.9%][r=28.8MiB/s,w=42.9MiB/s][r=7365,w=10.0k IOPS][eta 0Jobs: 1 (f=1): [m(1)][96.6%][r=28.1MiB/s,w=41.3MiB/s][r=7206,w=10.6k IOPS][eta 0Jobs: 1 (f=1): [m(1)][98.3%][r=28.2MiB/s,w=42.1MiB/s][r=7226,w=10.8k IOPS][eta 0Jobs: 1 (f=1): [m(1)][100.0%][r=28.7MiB/s,w=43.0MiB/s][r=7349,w=11.0k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2328: Sat Dec  2 05:37:14 2017
   read: IOPS=7146, BW=27.9MiB/s (29.3MB/s)(1639MiB/58704msec)
    slat (nsec): min=1521, max=1154.8k, avg=7984.06, stdev=5590.66
    clat (nsec): min=697, max=23382k, avg=222456.57, stdev=295907.78
     lat (usec): min=19, max=23387, avg=230.75, stdev=296.14
    clat percentiles (usec):
     |  1.00th=[   37],  5.00th=[  131], 10.00th=[  137], 20.00th=[  143],
     | 30.00th=[  149], 40.00th=[  153], 50.00th=[  159], 60.00th=[  165],
     | 70.00th=[  174], 80.00th=[  190], 90.00th=[  277], 95.00th=[  717],
     | 99.00th=[ 1188], 99.50th=[ 1663], 99.90th=[ 2409], 99.95th=[ 3523],
     | 99.99th=[10683]
   bw (  KiB/s): min=18432, max=30952, per=100.00%, avg=28586.52, stdev=1593.33, samples=117
   iops        : min= 4608, max= 7738, avg=7146.62, stdev=398.33, samples=117
  write: IOPS=10.7k, BW=41.9MiB/s (43.9MB/s)(2457MiB/58704msec)
    slat (nsec): min=1745, max=1031.6k, avg=8605.35, stdev=5513.44
    clat (nsec): min=833, max=18735k, avg=207058.16, stdev=271835.52
     lat (usec): min=71, max=18744, avg=215.98, stdev=272.07
    clat percentiles (usec):
     |  1.00th=[   90],  5.00th=[   99], 10.00th=[  105], 20.00th=[  116],
     | 30.00th=[  124], 40.00th=[  133], 50.00th=[  141], 60.00th=[  151],
     | 70.00th=[  161], 80.00th=[  182], 90.00th=[  269], 95.00th=[  644],
     | 99.00th=[ 1319], 99.50th=[ 1795], 99.90th=[ 2147], 99.95th=[ 3032],
     | 99.99th=[ 6587]
   bw (  KiB/s): min=26936, max=46272, per=99.99%, avg=42856.89, stdev=2368.17, samples=117
   iops        : min= 6734, max=11568, avg=10714.21, stdev=592.03, samples=117
  lat (nsec)   : 750=0.01%, 1000=0.01%
  lat (usec)   : 20=0.01%, 50=0.72%, 100=3.76%, 250=84.36%, 500=4.75%
  lat (usec)   : 750=1.84%, 1000=1.36%
  lat (msec)   : 2=3.05%, 4=0.10%, 10=0.03%, 20=0.01%, 50=0.01%
  cpu          : usr=7.26%, sys=18.99%, ctx=534006, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=419553,629023,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=27.9MiB/s (29.3MB/s), 27.9MiB/s-27.9MiB/s (29.3MB/s-29.3MB/s), io=1639MiB (1718MB), run=58704-58704msec
  WRITE: bw=41.9MiB/s (43.9MB/s), 41.9MiB/s-41.9MiB/s (43.9MB/s-43.9MB/s), io=2457MiB (2576MB), run=58704-58704msec

Disk stats (read/write):
  vda: ios=418284/627180, merge=0/11, ticks=88440/121444, in_queue=209600, util=98.48%
```

*file-size*
```
ls -al test4K-rw-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Dec  2 05:37 test4K-rw-aio
```

