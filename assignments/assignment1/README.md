# Assignment 1

Submit a text/pdf/markdown PDF to the [Canvas submission](https://ucsb.instructure.com/courses/22781/assignments/280728) that has answers to the 6 tasks described within this [notebook](./exploratory_data_analysis.ipynb).

### Task 1
Report the number of TCP/UDP/total packets contained within both files `pcaps/sample_speed_test.pcap` and `pcaps/speed_test.pcap`. Report the time it takes to read each pcap using the `scapy` library. 

### Task 2
Measure the time it takes to convert the file `pcaps/sample_speed_test.pcap` to a Pandas DataFrame. Estimate the time it will take to convert the file `pcaps/speed_test.pcap` to a Pandas DataFrame.

### Task 3
Report the number of unique 5-tuples, within `pcaps/speed_test.pcap`. 

### Task 4
Report the top 5 server IP(s) that send the most inbound data to the local client (192.168.0.203) and the top 5 server IP(s) that receive the most outbound data from the local client (192.168.0.203) in `pcaps/speed_test.pcap`.

### Task 5
Visualize the number of inbound and outbound bytes observed every second aggregated **over all flows** between the local IP (192.168.0.203) and the server IPs you identified in the previous task. 

### Task 6
Identify the flows that are relevant to the speed test. (Hint: The number of packets sent in each flow and the protocol are useful indicators for which servers are used for the speed test)

### Task 7
Estimate the duration of the upload and download portions of the speed test using the flows you identified in the previous task. The duration of the test would be the minimum window observed for all the flows until the maximum window observed for each window where we see a significant amount of full-sized packets (with len = 1500) between the client and server (e.g. ~ 1000 full-sized packets per second or more). Report the minimum time, maximum time, and duration.

### Task 8
For this task, you wil use a new windowing approach over all flows you identified relevant to the speed test for download and upload. Split the duration of the test into 20 windows, and aggregate the bytes over all relevant flows for each window. Report the total bytes measured over each of the 20 windows as well as the duration of each window for upload and download. (Hint: Use the `pd.cut` function to create a new column for this windowing approach)

### Task 9
Discard the windows with the 3 lowest and top 2 number of bytes. Estimate the download and upload throughput in Mbps from these 15 windows, where throughput is bytes divided by duration. (Hint: The duration of each window is equal to the duration of the speedtest divided by 20. Therefore the new duration to use for the throughput calcuation for the 15 windows is equal to 0.75 times the duration of the download / upload test you reported in Task 7.)

