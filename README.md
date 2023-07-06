# Pritntf_Scanf_Stm32

![image](https://github.com/Wneq1/Pritntf_Scanf_Stm32/assets/127328405/a47097c0-59bd-464c-82da-3aaa9a9869ea)
W celu wygodnego korzystania z funkcji Printf oraz Scanf można skorzystac z gotowego rozwiazania 
https://shawnhymel.com/1873/how-to-use-printf-on-stm32/
Oto kilka kroków:
1. Umiescic pliki c i h w odpowiednich folderach
 ![image](https://github.com/Wneq1/Pritntf_Scanf_Stm32/assets/127328405/f8240c2b-ee55-4d0a-8ec0-33bc762cc305)
2. Odpowiednio skonfigurować plik syscall.c
![image](https://github.com/Wneq1/Pritntf_Scanf_Stm32/assets/127328405/f35449d4-4f26-4798-bfaa-0c5055158006)
3. Napisac odpowiedni program w C:

Kod Programu:
/* Includes ------------------------------------------------------------------*/
#include "main.h"

/* Private includes ----------------------------------------------------------*/
/* USER CODE BEGIN Includes */
#include "retarget.h"
#include <stdio.h>
/* USER CODE END Includes */

/* Private typedef -----------------------------------------------------------*/
/* USER CODE BEGIN PTD */

/* USER CODE END PTD */

/* Private define ------------------------------------------------------------*/
/* USER CODE BEGIN PD */

/* USER CODE END PD */

/* Private macro -------------------------------------------------------------*/
/* USER CODE BEGIN PM */

/* USER CODE END PM */

/* Private variables ---------------------------------------------------------*/
UART_HandleTypeDef huart2;

/* USER CODE BEGIN PV */

/* USER CODE END PV */

/* Private function prototypes -----------------------------------------------*/
void SystemClock_Config(void);
static void MX_GPIO_Init(void);
static void MX_USART2_UART_Init(void);
/* USER CODE BEGIN PFP */

/* USER CODE END PFP */

/* Private user code ---------------------------------------------------------*/
/* USER CODE BEGIN 0 */

/* USER CODE END 0 */

/**
  * @brief  The application entry point.
  * @retval int
  */
int main(void)
{
  /* USER CODE BEGIN 1 */
	char buf[100];
  /* USER CODE END 1 */

  /* MCU Configuration--------------------------------------------------------*/

  /* Reset of all peripherals, Initializes the Flash interface and the Systick. */
  HAL_Init();

  /* USER CODE BEGIN Init */

  /* USER CODE END Init */

  /* Configure the system clock */
  SystemClock_Config();

  /* USER CODE BEGIN SysInit */

  /* USER CODE END SysInit */

  /* Initialize all configured peripherals */
  MX_GPIO_Init();
  MX_USART2_UART_Init();
  /* USER CODE BEGIN 2 */
RetargetInit(&huart2);
  /* USER CODE END 2 */

  /* Infinite loop */
  /* USER CODE BEGIN WHILE */
  while (1)
  {
    /* USER CODE END WHILE */

    /* USER CODE BEGIN 3 */
	  printf("\r\nYour name: ");
	    scanf("%s", buf);
	    printf("\r\nHello, %s!\r", buf);
  }
  /* USER CODE END 3 */
}
