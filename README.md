# ANY_ArduCam
Hardware Agnostic Driver for using the OV2640 based ArduCam. This library is currently friendly to low level embedded platforms. This is currently not a full featured as the original ArduCam arduino library supports many camera platforms as well as has other image format. Currently the only support image format for this platform is 
JPEG. Other functionality should be easy to add. This code was adpated from their ESP32 example. 

## Why?
Currently, all of the available libraries for this camera are all platform specific (arduino, ESP32, raspberry pi) so there would be a significant amount of dev effort involved to port over to another platform. With this repo, I've partially made it usable on any system via funtion pointers so that the end user only needs to provide hardware specific functions in order to get it working on their MCU.

## Original Library
My code was adapated from the below repo
https://github.com/ArduCAM/ArduCAM_ESP8266_UNO

## Demonstrated Embedded Platforms 
* TI CC3235 ( Wifi SoC) 

## How to Use
```
void main(void *arg0)
{

    ArduCam_t acam;
    acam.spi_write = acam_spi_write;
    acam.spi_read = acam_spi_read;
    acam.spi_cs_low = acam_spi_cs_low;
    acam.spi_cs_high = acam_spi_cs_high;
    acam.i2c_write = i2c_write;
    acam.i2c_read = i2c_read;
    acam.delay_ms = acam_delay_ms;

    ACAM_Init(&acam);
    ACAM_OV2640_set_JPEG_size(&acam,OV2640_320x240);

    ACAM_clear_fifo_flag(&acam);

    while(1){
        ACAM_clear_fifo_flag(&acam);
        ACAM_start_capture(&acam);

        /* wait for a capture to finish */
        while(!ACAM_get_bit(&acam,ARDUCHIP_TRIG, CAP_DONE_MASK));
        camCapture(&acam);
        Task_sleep(1);
    }

}
```
