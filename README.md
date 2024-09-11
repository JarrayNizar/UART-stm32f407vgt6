# UART-stm32f407vgt6
The project transfers the string "nizar" between the boards using interrupt and DMA modes for data handling.

Modes Used:

# Interrupt Mode:

Transmission: The orange and blue LEDs blink while the data is being sent. Once the transmission is complete, the green LED lights up, controlled by the HAL_UART_TxCpltCallback.
Reception: On the receiving board, the orange and blue LEDs blink during data reception, and the green LED confirms successful data reception via the HAL_UART_RxCpltCallback. In case of an error, the red LED lights up.
# DMA Mode:

Transmission: Data from the TX_Buffer is automatically transferred to UART_TX_DR using DMA. The green LED indicates successful transmission, while the red LED lights up in case of an error.
Reception: DMA transfers data from UART_RX_DR to memory. Once reception is complete, the green LED lights up, and errors are indicated by the red LED.
Peripherals Used:

UART: Manages asynchronous data communication.
RCC: Configures clock signals for stable operation.
NVIC: Manages interrupts for efficient handling.
GPIO: Controls the LEDs for visual status feedback.
Importance of Callbacks:

HAL_UART_TxCpltCallback: This callback is triggered when the UART transmission is complete. It is essential to ensure the system knows that the data has been fully transmitted, allowing the green LED to light up as confirmation. This ensures system synchronization and prevents data loss.
HAL_UART_RxCpltCallback: This callback is triggered when data is received. It is crucial for verifying the accuracy of the received data and triggers the green LED on successful reception. In case of failure, it activates the red LED, helping with error detection and correction.
