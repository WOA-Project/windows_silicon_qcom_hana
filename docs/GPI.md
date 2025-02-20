# Qualcomm Generic Peripheral Interface

The Qualcomm Generic Peripheral Interface (or GPI) is a middle man firmware sitting between the HWIO/FIFO direct memory access Qualcomm Universal Peripheral (QUP) interfaces, and a client, in order to support greater security permissions as well as simultaneous access from multiple clients (HLOS, DSPs etc).

## GPI Index (GPII) Assignments for MTP8150

The Qualcomm Technologies Incorporated Mobile Testing Platform for SM8150 (MTP8150) makes use of the following Buses:

- I2C5
- I2C8
- IC10
- SPI4
- UARD
- UR14
- UR18
- UR20

Their configuration and GPII assignment are as follows:

| QUP  | GPII | Clients | Bus  | Operation Mode | Notes                       |
|------|------|---------|------|----------------|-----------------------------|
| QUP0 | 0    |         |      |                |                             |
| QUP0 | 1    | HLOS    | SPI4 | GPI            | CODEC-WCD936x / WCD9340 SPI |
| QUP0 | 2    |         |      |                |                             |
| QUP0 | 3    |         |      |                |                             |
| QUP0 | 4    | HLOS    | I2C5 | FIFO           | FSA4480 / SMB1355 / SMB1390 |
| QUP0 | 5    |         |      |                |                             |
| QUP0 | 6    |         |      |                |                             |
| QUP0 | 7    | HLOS    | I2C8 | FIFO           | OEM Dock I/O                |
| QUP0 | 8    |         |      |                |                             |
| QUP0 | 9    |         |      |                |                             |
| QUP0 | 10   |         |      |                |                             |
| QUP0 | 11   |         |      |                |                             |
| QUP0 | 12   |         |      |                |                             |

| QUP  | GPII | Clients | Bus  | Operation Mode | Notes                       |
|------|------|---------|------|----------------|-----------------------------|
| QUP1 | 0    |         |      |                |                             |
| QUP1 | 1    | HLOS    | IC10 | FIFO           | NFC Sensor                  |
| QUP1 | 2    |         |      |                |                             |
| QUP1 | 3    | HLOS    | UARD | GPI            | UART Debug port             |
| QUP1 | 4    | HLOS    | UR14 | GPI            | Housekeeping (GPIOs 83, 84) |
| QUP1 | 5    |         |      |                |                             |
| QUP1 | 6    |         |      |                |                             |
| QUP1 | 7    |         |      |                |                             |
| QUP1 | 8    |         |      |                |                             |
| QUP1 | 9    |         |      |                |                             |
| QUP1 | 10   |         |      |                |                             |
| QUP1 | 11   |         |      |                |                             |
| QUP1 | 12   |         |      |                |                             |

| QUP  | GPII | Clients | Bus  | Operation Mode | Notes                       |
|------|------|---------|------|----------------|-----------------------------|
| QUP2 | 0    |         |      |                |                             |
| QUP2 | 1    | HLOS    | UR18 | GPI            | attached to BT SOC          |
| QUP2 | 2    |         |      |                |                             |
| QUP2 | 3    | HLOS    | UR20 | GPI            | HS - 5G (GPIOs 29, 30)      |
| QUP2 | 4    |         |      |                |                             |
| QUP2 | 5    |         |      |                |                             |
| QUP2 | 6    |         |      |                |                             |
| QUP2 | 7    |         |      |                |                             |
| QUP2 | 8    |         |      |                |                             |
| QUP2 | 9    |         |      |                |                             |
| QUP2 | 10   |         |      |                |                             |
| QUP2 | 11   |         |      |                |                             |
| QUP2 | 12   |         |      |                |                             |

And is reflected in driver configuration as such:

---

- I2C:
    - QUP0:
        - I2C5:

```
Address: 0x00890000
Instance: 5
Resource: QUPV3_ID0_SE5
```

```ini
HKR, Instance\5, "GPII",    %REG_DWORD%, 4
HKR, Instance\5, "OpMode",  %REG_DWORD%, %OP_MODE_FIFO%
HKR, Instance\5, "QUPType", %REG_DWORD%, %QUP_0%
```

---

- I2C:
    - QUP0:
        - I2C8:

```
Address: 0x0089c000
Instance: 8
Resource: QUPV3_ID0_SE8
```

```ini
HKR, Instance\8,  "GPII",    %REG_DWORD%, 7
HKR, Instance\8,  "OpMode",  %REG_DWORD%, %OP_MODE_FIFO%
HKR, Instance\8,  "QUPType", %REG_DWORD%, %QUP_0%
```

---

- I2C:
    - QUP1:
        - IC10:

```
Address: 0x00a84000
Instance: 10
Resource: QUPV3_ID1_SE2
```

```ini
HKR, Instance\10, "GPII",    %REG_DWORD%, 1
HKR, Instance\10, "OpMode",  %REG_DWORD%, %OP_MODE_FIFO%
HKR, Instance\10, "QUPType", %REG_DWORD%, %QUP_1%
```

---

- SPI:
    - QUP0:
        - SPI4:

```
Address: 0x0088C000
Instance: 4
Resource: QUPV3_ID0_SE4
```

```ini
HKR, Instance\4, "GPII",     %REG_DWORD%, 1
HKR, Instance\4, "OpMode",   %REG_DWORD%, %OP_MODE_GPI%
HKR, Instance\4, "QUPBlock", %REG_DWORD%, %QUP_0%
```

---

- UART:
    - QUP1:
        - UARD:

```
Address: 0x00A90000
Instance: 13
Resource: QUPV3_ID1_SE5
```

```ini
HKR, Instance\13, "UartClass",     %REG_DWORD%, 0x2
HKR, Instance\13, "EnableGsi",     %REG_DWORD%, 0x0
HKR, Instance\13, "GpiiId",        %REG_DWORD%, 0x3
HKR, Instance\13, "DeleteComPort", %REG_DWORD%, 0x0
```

---

- UART:
    - QUP1:
        - UR14:

```
Address: 0x00A94000
Instance: 14
Resource: QUPV3_ID1_SE6
```

```ini
HKR, Instance\14, "UartClass",     %REG_DWORD%, 0x2
HKR, Instance\14, "EnableGsi",     %REG_DWORD%, 0x0
HKR, Instance\14, "GpiiId",        %REG_DWORD%, 0x4
HKR, Instance\14, "DeleteComPort", %REG_DWORD%, 0x0
```

---

- UART:
    - QUP2:
        - UR18:

```
Address: 0x00C8C000
Instance: 18
Resource: QUPV3_ID2_SE4
```

```ini
HKR, Instance\18, "UartClass",     %REG_DWORD%, 0x2
HKR, Instance\18, "EnableGsi",     %REG_DWORD%, 0x0
HKR, Instance\18, "GpiiId",        %REG_DWORD%, 0x1
HKR, Instance\18, "DeleteComPort", %REG_DWORD%, 0x1
```

---

- UART:
    - QUP2:
        - UR20:

```
Address: 0x00C94000
Instance: 20
Resource: QUPV3_ID2_SE6
```

```ini
HKR, Instance\20, "UartClass",     %REG_DWORD%, 0x2
HKR, Instance\20, "EnableGsi",     %REG_DWORD%, 0x0
HKR, Instance\20, "GpiiId",        %REG_DWORD%, 0x3
HKR, Instance\20, "DeleteComPort", %REG_DWORD%, 0x0
```