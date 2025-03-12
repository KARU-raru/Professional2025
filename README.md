# Professional2025
Arduino подсветка 

#include <Adafruit_NeoPixel.h>

#define LED_PIN 6
#define LED_COUNT 10

Adafruit_NeoPixel strip(LED_COUNT, LED_PIN, NEO_GRB + NEO_KHZ800);

void setup() {
  strip.begin();
  strip.show();
 
  // Задаем начальный цвет - зеленый
  setColor(GREEN);
}

void loop() {
  // В зависимости от состояния робота устанавливаем цвет ленты
  switch (robotState) {
    case WAITING_FOR_PICKUP:
      setColor(GREEN);
      break;
    case MOVING:
      setColor(YELLOW);
      break;
    case WAITING_FOR_DELIVERY:
      setColor(RED);
      break;
  }
 
  // Обновляем состояние ленты
  strip.show();
}

void setColor(uint32_t color) {
  for (int i = 0; i < LED_COUNT; i++) {
    strip.setPixelColor(i, color);
  }
}

// Функции для определения состояния робота (WAITING_FOR_PICKUP, MOVING, WAITING_FOR_DELIVERY)

// ...
