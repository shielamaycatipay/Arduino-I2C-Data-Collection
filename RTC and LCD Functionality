#include <Wire.h>
#include <RTClib.h>
#include <LiquidCrystal_I2C.h>

RTC_DS1307 rtc;
LiquidCrystal_I2C lcd(0x27, 16, 2);

bool rtcAvailable = false;

void printTwoDigits(int num) {
  if (num < 10) lcd.print("0");
  lcd.print(num);
}

void setup() {
  Serial.begin(115200);
  delay(2000);
  Wire.begin(21, 22);

  lcd.begin(16, 2);
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("System Starting");
  Serial.println("LCD initialized at 0x27");

  if (rtc.begin()) {
    rtcAvailable = true;
    Serial.println("RTC detected at 0x68");
    if (!rtc.isrunning()) {
      rtc.adjust(DateTime(F(__DATE__), F(__TIME__)));
    }
  } else {
    Serial.println("RTC NOT detected");
  }

  delay(2000);
  lcd.clear();
}

void loop() {
  Serial.println("---- SYSTEM STATUS ----");
  Serial.println("LCD: OK  (0x27)");

  if (rtcAvailable) {
    DateTime now = rtc.now();

    lcd.setCursor(0, 0);
    lcd.print("DATE:");
    printTwoDigits(now.month());
    lcd.print("/");
    printTwoDigits(now.day());
    lcd.print("/");
    lcd.print(now.year());

    lcd.setCursor(0, 1);
    lcd.print("TIME:");
    printTwoDigits(now.hour());
    lcd.print(":");
    printTwoDigits(now.minute());
    lcd.print(":");
    printTwoDigits(now.second());

    Serial.print("RTC (0x68) Date : ");
    Serial.print(now.year());
    Serial.print("/");
    Serial.print(now.month());
    Serial.print("/");
    Serial.println(now.day());

    Serial.print("RTC (0x68) Time : ");
    Serial.print(now.hour());
    Serial.print(":");
    Serial.print(now.minute());
    Serial.print(":");
    Serial.println(now.second());

    Serial.print("Unix Timestamp  : ");
    Serial.println(now.unixtime());

  } else {
    lcd.setCursor(0, 0);
    lcd.print("DATE: N/A       ");
    lcd.setCursor(0, 1);
    lcd.print("RTC NOT DETECTED");
    Serial.println("RTC: NOT DETECTED");
  }

  Serial.println("-----------------------");
  delay(1000);
}
