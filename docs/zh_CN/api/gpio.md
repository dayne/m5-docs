# I/O (GPIO/ADC/DAC/PWM)

*Refer to Arduino API of [Arduino](http://www.arduino.cc)*

*为方便起见，我将专注于与M5Stack 密切相关的事情*

**M5STACK 引脚排列:**
	
| pin No | Name |allocation|
| ---  |  --- |   ---    |
|    0 |  G0  |downloader |
|    1 |  T1  |UART      |
|    2 |  G2  |Side terminal (except M5FIRE),M5-BUS|
|    3 |  R1  |UART     |
|    4 |  G4  |TF|
|    5 |  G5  |Side terminal (except M5FIRE),M5-BUS|
|    6 |  G6 |SDIO      |
|    7 |  G7 |SDIO      |
|    8 |  G8 |SDIO      |
|    9 |  G9 |SDIO      |
|   10 |  G10 |SDIO      |
|   11 |  G11 |SDIO      |
|   12 |  G12 |LCD      |
|   13 |  G13 |LCD      |
|   14 |  G14 |LCD      |
|   15 |  G15 |LCD      |
|   16 |  R2 |UART      |
|   17 |  T2 |UART     |
|   18 |  G18 |TF,Top terminal(SCK),M5-BUS|
|   19 |  G19 |TF,Top terminal(MISO),M5-BUS|
|   21 |  G21 |GROVE-A(SDA)|
|   22 |  G22 |GROVE-A(SCL)|
|   23 |  G23 |TF,Top terminal(MOSI)|
|   25 |  G25 |Speaker,Side terminal (except M5FIRE),M5-BUS|
|   26 |  G26 |Side terminal (except M5FIRE),M5-BUS|
|   27 |  G27 |LCD      |
|   32 |  G32 |LCD BackLight |
|   33 |  G33 |LCD      |
|   34 |  G34 |None      |
|   35 |  G35 |Side terminal (except M5FIRE)|
|   36 |  G36 |Side terminal (except M5FIRE)|
|   37 |  G37 |Button C|
|   38 |  G38 |Button B|
|   39 |  G39 |Button A|


## digitalRead()

**函数原型:**

<mark>int digitalRead(uint8_t pin);</mark>

**功能:**

读取终端的状态。

**参数**
	
| 参数 | 类型 | 描述 |
| --- | --- | --- |
| pin | <code>uint8</code> |Pin No |

**返回值:**

引脚输入状态（0/1）

**注意**

1）如果引脚模式未设置为INPUT，则不会返回正确的结果。

2）如果控制线中有其他电路，它们将受到影响。

**使用示例;**

```arduino
uint32_t pin21_data;
pin21_data = digitalRead(21);
```

## digitalWrite()

**函数原型:**

<mark>void digitalWrite(uint8_t pin, uint8_t val);</mark>

**功能:**

指示终端的输出

**参数**
	
| 参数 | 类型 | 描述 |
| --- | --- | --- |
| pin | <code>uint8</code> |pin No |
| val | <code>uint8</code> |输出状态(0/1) |

**返回值:**

无。

**注意**
	
1）如果终端模式未设置为OUTPUT，则不会返回正确的结果。

2）请注意，如果控制线中有其他电路，则可能会造成物理损坏。

**使用示例;**

```arduino
digitalWrite(2,1);
```

## pinMode()

**函数原型:**

<mark>void pinMode(uint8_t pin, uint8_t mode);</mark>

**功能:**

设置终端输入/输出模式。

**参数**
	
| 参数 | 类型 | 描述 |
| --- | --- | --- |
| pin | <code>uint8</code> |pin No |
| mode | <code>uint8</code> |INPUT,OUTPUT,INPUT_PULLUP 的任何一个|

**返回值:**

无。

**注意**

如果总线上有其他电路，请注意可能存在物理损坏。

例如，当扬声器（G25）端子设置为INPUT模式时，流向扬声器的电流使主单元产生热量。

确保操作正确，因为存在损坏风险。

**使用示例;**

```arduino
pinMode(2,INPUT);
```

## analogRead()

**函数原型:**
<mark>uint16_t analogRead(uint8_t pin);</mark>

**功能:**

读取模拟终端的值。

**参数**
	
| 参数 | 类型 | 描述 |
| --- | --- | --- |
| pin | <code>uint8</code> |pin No |

**返回值:**

阅读结果。响应的最大值由analogSetWidth()确定。

**注意**

G35和G36可用于M5Stack。

**使用示例;**

```arduino
uint16_t ret;
ret=analogRead(35);
```

## dacWrite()

**函数原型:**

<mark>void dacWrite(uint8_t pin, uint8_t value);</mark>

**功能:**

输出命令到模拟端子。

**参数**
	
| 参数 | 类型 | 描述 |
| --- | --- | --- |
| pin | <code>uint8</code> |pin No |
| value | <code>uint8</code> |设定输出电压 |

**返回值:**

无。。

**注意**

G25和G26可用于M5Stack。

**使用示例;**

```arduino
dacWrite(25,0x40);
```

## ledcSetup()

**函数原型:**

<mark>double ledcSetup(uint8_t channel, double freq, uint8_t resolution_bits);</mark>

**功能:**

设置占空比输出

**参数**
	
| 参数 | 类型 | 描述 |
| --- | --- | --- |
| channel | <code>uint8</code> |channel (0～15) |
| freq | <code>double</code> |frequency (Hz) |
| resolution_bits | <code>uint8_t</code> |占空比指示的满量程位数|

**返回值:**

Actual output frequency.

**注意**

通道和GPIO端口号不相同。

它应该被识别为用于存储设置的数字。


## ledcAttachPin()

**函数原型:**

<mark>void ledcAttachPin(uint8_t pin, uint8_t chan);</mark>

**功能:**

指定引脚.

**参数**
	
| 参数 | 类型 | 描述 |
| --- | --- | --- |
| pin | <code>uint8_t</code> |pin No) |
| chan | <code>uint8_t</code> |渠道(0～15) |

**返回值:**

无。


## ledcWrite()

**函数原型:**

<mark>void ledcWrite(uint8_t chan, uint32_t duty);</mark>

**功能:**

输出具有指定的占空比值

**参数**
	
| 参数 | 类型 | 描述 |
| --- | --- | --- |
| chan | <code>uint8_t</code> |渠道(0～15) |
| duty | <code>uint32_t</code> |比 |

**返回值:**

无。

**注意**

占空比取决于初始化时设置的位比例。

使用8位指定时，指定0xFF会导致100％输出。


## ledcDetachPin()

**函数原型:**

<mark>void ledcDetachPin(uint8_t pin);</mark>

**功能:**

释放指定的端口并停止输出。

**参数**
	
| 参数 | 类型 | 描述 |
| --- | --- | --- |
| pin | <code>uint8_t</code> |pin No |


**返回值:**

无。

## adcAttachPin()

**函数原型:**

<mark>bool adcAttachPin(uint8_t pin)</mark>

**功能:**

非阻塞模式.连接设定引脚到ADC .

**函数参数**
	
| 函数参数 | 类型 | 描述 |
| --- | --- | --- |
| pin | uint8_t | 指定引脚 |

**函数返回值:**

设置成功返回1

## adcBusy()

**函数原型:**

<mark>bool adcBusy(uint8_t pin)</mark>

**功能:**

非阻塞模式,检查adc转换是否进行中.

**函数参数**
	
| 函数参数 | 类型 | 描述 |
| --- | --- | --- |
| pin | uint8_t | 指定引脚 |

**函数返回值:**

转换中返回1

## adcEnd()

**函数原型:**

<mark>uint16_t adcEnd(uint8_t pin)</mark>

**功能:**

非阻塞模式,返回转换结果,如果未转换完成等待完成.

**函数参数**
	
| 函数参数 | 类型 | 描述 |
| --- | --- | --- |
| pin | uint8_t | 指定引脚 |

**函数返回值:**

返回转换结果

## adcStart()

**函数原型:**

<mark>bool adcStart(uint8_t pin)</mark>

**功能:**

非阻塞模式,开启adc转换.

**函数参数**
	
| 函数参数 | 类型 | 描述 |
| --- | --- | --- |
| pin | uint8_t | 指定引脚 |

**函数返回值:**

成功开启返回1


## analogReadResolution()

**函数原型:**

<mark>void analogReadResolution(uint8_t bits)</mark>

**功能:**

设置模拟数据读取分辨率，取值1~16，默认为12。如果介于9和12之间，它将等于设置的硬件分辨率，否则值将被移动.

**函数参数**
	
| 函数参数 | 类型 | 描述 |
| --- | --- | --- |
| bits | uint8_t | 采样分辨率 |

**函数返回值:**

None

## analogSetAttenuation()

**函数原型:**

<mark>void analogSetAttenuation(adc_attenuation_t attenuation)</mark>

**功能:**

设置ADC全局输入衰减，取值ADC_0db, ADC_2_5db, ADC_6db, ADC_11db，默认为11db

**函数参数**
	
| 函数参数 | 类型 | 描述 |
| --- | --- | --- |
| attenuation | adc_attenuation_t | 衰减值 |

**函数返回值:**

None

## analogSetCycles()

**函数原型:**

<mark>void analogSetCycles(uint8_t cycles)</mark>

**功能:**

设置采样周期1-255,默认为8.

**函数参数**
	
| 函数参数 | 类型 | 描述 |
| --- | --- | --- |
| cycles | uint8_t | sampling period |

**函数返回值:**

None

## analogSetPinAttenuation()

**函数原型:**

<mark>void analogSetPinAttenuation(uint8_t pin, adc_attenuation_t attenuation)</mark>

**功能:**

设置某个单独引脚衰减

**函数参数**
	
| 函数参数 | 类型 | 描述 |
| --- | --- | --- |
| pin | uint8_t | specified pin |
| attenuation | adc_attenuation_t | 衰减值 |

**函数返回值:**

None

## analogSetSamples()

**函数原型:**

<mark>void analogSetSamples(uint8_t samples)</mark>

**功能:**

设置单次采样的实际采样倍数,取值1-255,默认为1,实际效果为提高adc灵敏度,采样次数扩大N倍;

**函数参数**
	
| 函数参数 | 类型 | 描述 |
| --- | --- | --- |
| samples | uint8_t | 采样倍数 |

**函数返回值:**

None

## analogSetWidth()

**函数原型:**

<mark>void analogSetWidth(uint8_t bits)</mark>

**功能:**

设置adc采样分辨率9-12,默认为12.

**函数参数**
	
| 函数参数 | 类型 | 描述 |
| --- | --- | --- |
| bits | uint8_t | 采样分辨率 |

**函数返回值:**

None

## attachInterrupt()

**函数原型:**

<mark>void attachInterrupt(pin, ISR(callback function), interrupt type/mode)</mark>

**功能:**

设置引脚中断.

**函数参数**
	 
| 函数参数 | 类型 | 描述 |
| --- | --- | --- |
| pin | uint8_t | 引脚 |
| ISR | callcack function | 回调函数 |
| interrupt | mode | 触发类型 |

**函数返回值:**

None.

## detachInterrupt()

**函数原型:**

<mark>void detachInterrupt(pin)</mark>

**功能:**

Prohibit specified pin interruptio.

**函数参数**
	
| 函数参数 |类型 |功能 |
| --- | --- | --- |
| pin | uint8_t | pin No. |

**函数返回值:**

None.

## hallRead()

**函数原型:**

<mark>int hallRead(void));</mark>

**功能:**

读取霍尔传感器.

**函数参数**
	
None

**函数返回值:**

int.

## ledcRead()

**函数原型:**

<mark>uint32_t ledcRead(uint8_t channel)</mark>

**功能:**

返回指定通道的占空比.

**函数参数**
	
| 函数参数 | 类型 | 描述 |
| --- | --- | --- |
| channel | uint8_t | 指定通道 |

**函数返回值:**

占空比

## ledcReadFreq()

**函数原型:**

<mark>double ledcReadFreq(uint8_t channel)</mark>

**功能:**

返回当前通道频率.

**函数参数**
	
| 函数参数 |类型 | 描述 |
| --- | --- | --- |
| channel | uint8_t | 指定通道 |

**函数返回值:**

通道频率