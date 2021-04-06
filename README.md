# Pico Ping

Uses [lwIP](https://www.nongnu.org/lwip/2_0_x/index.html) in combination with the ENC28J60 SPI ethernet module to bring a TCP/IP stack to the Pi Pico!

Packets are read from SPI and then fed to lwIP which is running in "NO_SYS" mode - because
the Pi Pico has no operating system! Pseudo code for this approach can be [found here](https://www.nongnu.org/lwip/2_0_x/group__lwip__nosys.html).

Code to interact with the ethernet module was adapted from an @turicas's [Arduino driver](https://github.com/turicas/Ethernet_ENC28J60).

![Image of Pico responding to ping over local IP address](/pico-ping.png)

# Future Improvements

- [ ] diagram of wiring
- [ ] format code
- [ ] get DHCP discovery working
