# Aidon/Hafslund AMS data parser

Use with an M-Bus dongle such as [this one](https://www.aliexpress.com/item/USB-to-MBUS-slave-module-MBUS-master-slave-communication-debugging-bus-monitor-TSS721-No-spontaneity-Self/32894249052.html).

### aidon_obis.py
A class for decoding HDLC and extracting OBIS fields. Requires python module crcmod (sudo pip install crcmod).
*NB: This is not a full COSEM parser, as the number of OBIS fields and their sequence is assumed to be as on a Hafslund meter.*

### aidon_test.py
Test output <br/>
`./aidon_test.py <port>` <br/>
`./aidon_test.py /dev/ttyUSB0` <br/>

### aidon_forward.py
Forward to influxdb and Home Assistant. <br/>
Forwarding to only one of them is possible. Just omit the influx* or hass* arguments. <br/>
`python aidon_forward.py \
/dev/ttyUSB0 \
--influx_host http://localhost:8086 \
--influx_db metering \
--hass_host https://myhass.com:8123 \
--hass_token abcdefgh0123456789`

### aidon_read.py
Parses preliminary/old protocol used by Hafslund. <br/>
`./aidon_read.py /dev/ttyUSB0` <br/>
