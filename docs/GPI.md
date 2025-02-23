# Qualcomm Generic Peripheral Interface

The Qualcomm Generic Peripheral Interface (or GPI) is a middle man firmware sitting between the HWIO/FIFO direct memory access Qualcomm Universal Peripheral (QUP) interfaces, and a client, in order to support greater security permissions as well as simultaneous access from multiple clients (HLOS, DSPs etc).

## Bus Summary

SM8150 Contains 4 QUPs, with the following SEs available for each:

---

QUPv3 South:

| Si             | QUP  | SE | Address    | Length     | IRQ | Android DT Names             |
|----------------|------|----|------------|------------|-----|------------------------------|
| QUPV3_WRAP0_S0 | QUP0 | 0  | 0x00880000 | 0x00004000 | 601 | qupv3_se0_i2c, qupv3_se0_spi |
| QUPV3_WRAP0_S1 | QUP0 | 1  | 0x00884000 | 0x00004000 | 602 | qupv3_se1_i2c, qupv3_se1_spi |
| QUPV3_WRAP0_S2 | QUP0 | 2  | 0x00888000 | 0x00004000 | 603 | qupv3_se2_i2c, qupv3_se2_spi |
| QUPV3_WRAP0_S3 | QUP0 | 3  | 0x0088C000 | 0x00004000 | 604 | qupv3_se3_i2c, qupv3_se3_spi |
| QUPV3_WRAP0_S4 | QUP0 | 4  | 0x00890000 | 0x00004000 | 605 | qupv3_se4_i2c, qupv3_se4_spi |
| QUPV3_WRAP0_S5 | QUP0 | 5  | 0x00894000 | 0x00004000 | 606 | qupv3_se5_i2c, qupv3_se5_spi |
| QUPV3_WRAP0_S6 | QUP0 | 6  | 0x00898000 | 0x00004000 | 607 | qupv3_se6_i2c, qupv3_se6_spi |
| QUPV3_WRAP0_S7 | QUP0 | 7  | 0x0089C000 | 0x00004000 | 608 | qupv3_se7_i2c, qupv3_se7_spi |

---

QUPv3 North:

| Si             | QUP  | SE | Address    | Length     | IRQ | Android DT Names                                 |
|----------------|------|----|------------|------------|-----|--------------------------------------------------|
| QUPV3_WRAP1_S0 | QUP1 | 8  | 0x00A80000 | 0x00004000 | 353 | qupv3_se8_i2c, qupv3_se8_spi                     |
| QUPV3_WRAP1_S1 | QUP1 | 9  | 0x00A84000 | 0x00004000 | 354 | qupv3_se4_2uart, qupv3_se9_i2c, qupv3_se9_spi    |
| QUPV3_WRAP1_S2 | QUP1 | 10 | 0x00A88000 | 0x00004000 | 355 | qupv3_se10_i2c, qupv3_se10_spi                   |
| QUPV3_WRAP1_S3 | QUP1 | 11 | 0x00A8C000 | 0x00004000 | 356 | qupv3_se11_i2c, qupv3_se11_spi                   |
| QUPV3_WRAP1_S4 | QUP1 | 12 | 0x00A90000 | 0x00004000 | 357 | qupv3_se12_2uart, qupv3_se12_i2c, qupv3_se12_spi |
| QUPV3_WRAP1_S5 | QUP1 | 16 | 0x00A94000 | 0x00004000 | 358 | qupv3_se16_i2c, qupv3_se16_spi                   |

---

QUPv3 East:

| Si             | QUP  | SE | Address    | Length     | IRQ | Android DT Names                                 |
|----------------|------|----|------------|------------|-----|--------------------------------------------------|
| QUPV3_WRAP2_S0 | QUP2 | 17 | 0x00C80000 | 0x00004000 | 373 | qupv3_se17_i2c, qupv3_se17_spi                   |
| QUPV3_WRAP2_S1 | QUP2 | 18 | 0x00C84000 | 0x00004000 | 583 | qupv3_se18_i2c, qupv3_se18_spi                   |
| QUPV3_WRAP2_S2 | QUP2 | 19 | 0x00C88000 | 0x00004000 | 584 | qupv3_se19_i2c, qupv3_se19_spi                   |
| QUPV3_WRAP2_S3 | QUP2 | 13 | 0x00C8C000 | 0x00004000 | 585 | qupv3_se13_4uart, qupv3_se13_i2c, qupv3_se13_spi |
| QUPV3_WRAP2_S4 | QUP2 | 14 | 0x00C90000 | 0x00004000 | 586 | qupv3_se14_i2c, qupv3_se14_spi                   |
| QUPV3_WRAP2_S5 | QUP2 | 15 | 0x00C94000 | 0x00004000 | 587 | qupv3_se15_i2c, qupv3_se15_spi                   |

---

QUPv3 SSC:

| Si             | QUP  | SE | Address    | Length     | IRQ | Android DT Names               |
|----------------|------|----|------------|------------|-----|--------------------------------|
| QUPV3_SE0      | QUP3 | 20 | 0x02680000 | 0x00004000 | 442 | qupv3_se20_i2c                 |
| QUPV3_SE1      | QUP3 | 21 | 0x02684000 | 0x00004000 | 443 | qupv3_se21_i2c, qupv3_se21_spi |
| QUPV3_SE2      | QUP3 | 22 | 0x02688000 | 0x00004000 | 444 | qupv3_se22_i2c, qupv3_se22_spi |
| QUPV3_SE3      | QUP3 | 23 | 0x0268C000 | 0x00004000 | 445 | qupv3_se23_i2c                 |

## Misc (MTP8150)

Available GPIIs:

| QUP  | GPII | Clients           |
|------|------|-------------------|
| QUP0 | 0    | ADSP              |
| QUP0 | 1    | HLOS / HLOS (GSI) |
| QUP0 | 2    | ADSP              |
| QUP0 | 3    | HLOS / HLOS (GSI) |
| QUP0 | 4    | HLOS / HLOS (GSI) |
| QUP0 | 5    | HLOS / HLOS (GSI) |
| QUP0 | 6    | HLOS / HLOS (GSI) |
| QUP0 | 7    | HLOS / HLOS (GSI) |
| QUP0 | 8    | TZ                |
| QUP0 | 9    | TZ                |
| QUP0 | 10   | ADSP              |
| QUP0 | 11   | ADSP              |
| QUP0 | 12   | MPSS              |

---

| QUP  | GPII | Clients           |
|------|------|-------------------|
| QUP1 | 0    | ADSP              |
| QUP1 | 1    | HLOS / HLOS (GSI) |
| QUP1 | 2    | ADSP              |
| QUP1 | 3    | HLOS / HLOS (GSI) |
| QUP1 | 4    | HLOS / HLOS (GSI) |
| QUP1 | 5    | HLOS / HLOS (GSI) |
| QUP1 | 6    | HLOS / HLOS (GSI) |
| QUP1 | 7    | HLOS / HLOS (GSI) |
| QUP1 | 8    | TZ                |
| QUP1 | 9    | TZ                |
| QUP1 | 10   | ADSP              |
| QUP1 | 11   | ADSP              |
| QUP1 | 12   | MPSS              |

---

| QUP  | GPII | Clients           |
|------|------|-------------------|
| QUP2 | 0    | ADSP              |
| QUP2 | 1    | HLOS / HLOS (GSI) |
| QUP2 | 2    | ADSP              |
| QUP2 | 3    | HLOS / HLOS (GSI) |
| QUP2 | 4    | HLOS / HLOS (GSI) |
| QUP2 | 5    | HLOS / HLOS (GSI) |
| QUP2 | 6    | HLOS / HLOS (GSI) |
| QUP2 | 7    | HLOS / HLOS (GSI) |
| QUP2 | 8    | TZ                |
| QUP2 | 9    | TZ                |
| QUP2 | 10   | ADSP              |
| QUP2 | 11   | ADSP              |
| QUP2 | 12   | MPSS              |

Bus Security:

| QUP  | SE | Bus           | Operation Mode | Owner | Can Operate in FIFO? | Load GPI FW? | TZ Exclusive Modification? | Notes                       |
|------|----|---------------|----------------|-------|----------------------|--------------|----------------------------|-----------------------------|
| QUP0 | 0  | SPI           | GSI            | TZ    | False                | True         | True                       | NFC eSE                     |
| QUP0 | 1  | I2C           | FIFO           | HLOS  | True                 | True         | False                      | SS Sub-PMIC                 |
| QUP0 | 2  | SPI           | GSI            | TZ    | False                | True         | True                       | Fingerprint                 |
| QUP0 | 3  | SPI           | GSI            | HLOS  | True                 | True         | False                      | WCD936x                     |
| QUP0 | 4  | I2C           | FIFO           | HLOS  | True                 | True         | False                      | Haptics (sensors hub)       |
| QUP0 | 6  | UART (2 wire) | FIFO           | HLOS  | True                 | True         | False                      | 5G HS-UART                  |
| QUP0 | 7  | I2C           | FIFO           | HLOS  | True                 | True         | False                      | SS PMIC                     |

---

| QUP  | SE | Bus           | Operation Mode | Owner | Can Operate in FIFO? | Load GPI FW? | TZ Exclusive Modification? | Notes                       |
|------|----|---------------|----------------|-------|----------------------|--------------|----------------------------|-----------------------------|
| QUP1 | 0  | SPI           | GSI            | HLOS  | True                 | True         | False                      | SS Camera                   |
| QUP1 | 1  | I2C           | GSI            | HLOS  | False                | True         | False                      | NFC / Forcetouch            |
| QUP1 | 3  | SPI           | GSI            | HLOS  | True                 | True         | False                      | SS Camera                   |
| QUP1 | 4  | UART (2 wire) | FIFO           | HLOS  | True                 | False        | False                      | Debug                       |
| QUP1 | 5  | UART (2 wire) | FIFO           | HLOS  | True                 | True         | False                      | Napier WiFi                 |

---

| QUP  | SE | Bus           | Operation Mode | Owner | Can Operate in FIFO? | Load GPI FW? | TZ Exclusive Modification? | Notes                       |
|------|----|---------------|----------------|-------|----------------------|--------------|----------------------------|-----------------------------|
| QUP2 | 0  | I2C           | FIFO           | HLOS  | True                 | True         | False                      | SS WPC                      |
| QUP2 | 2  | I2C           | FIFO           | HLOS  | True                 | True         | False                      | legacy touch                |
| QUP2 | 3  | UART (4 wire) | FIFO           | HLOS  | True                 | True         | False                      | BT HCI                      |

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