# UART-stm32f407vgt6
The project transfers the string "nizar" between the boards using interrupt and DMA modes for data handling.

# Interrupt Mode:
-Transmission: The orange and blue LEDs toggle while data is being sent. When transmission is complete, the green LED lights up, controlled by the HAL_UART_TxCpltCallback.
-Reception: On the receiving board, the orange and blue LEDs toggle during reception, and the green LED confirms successful data reception via the HAL_UART_RxCpltCallback. Any error lights up the red LED.
# DMA Mode:
-Transmission: Data from TX_Buffer is automatically transferred to UART_TX_DR using DMA. The green LED indicates successful transmission, while errors trigger the red LED.
-Reception: DMA transfers data from UART_RX_DR to memory. Upon completion, the green LED lights up, while errors are indicated by the red LED.
# Peripherals Used :
-UART: Manages asynchronous data communication.
-RCC: Configures clock signals for stable operation.
-NVIC: Manages interrupts for efficient handling. 
-GPIO: Controls LEDs for visual status feedback. 
# Callback Significance : 
-HAL_UART_TxCpltCallback: This callback is triggered when the UART transmission completes. It is essential for ensuring the system knows when the data has been fully transmitted, allowing the green LED to light up as a confirmation. This ensures the system is synchronized and avoids data loss.
-HAL_UART_RxCpltCallback: This callback is called when data is received. It is critical for checking the accuracy of the received data and triggers the green LED on successful reception. If the reception fails, it can activate the red LED, helping with error detection and correction.
