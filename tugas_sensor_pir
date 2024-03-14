#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

#define pirPin 12
int statusPir = LOW;
int gerakanPir;
int motioncount = 0;

void setup() {
  pinMode(pirPin, INPUT);
  lcd.init();
  lcd.backlight();
  
  // Inisialisasi LCD dengan teks awal
  lcd.setCursor(2,0);
  lcd.print("PRAKTIKUM 3:");
  lcd.setCursor(3,1);
  lcd.print("Sensor PIR");
  
  Serial.begin(9600);
  delay(4000); // Delay untuk memberi waktu LCD untuk inisialisasi
}

void loop() {
  gerakanPir = digitalRead(pirPin);
  
  // Cek jika gerakan terdeteksi
  if(gerakanPir == HIGH){
    delay(2000); // Delay untuk mengurangi false positives
    
    // Meningkatkan hitungan gerakan dan memperbarui LCD
    motioncount++;
    updateLCD();
    
    // Pesan Serial untuk debugging
    Serial.print("Motion Detect = ");
    Serial.println(motioncount);
    
    // Menampilkan pesan gerakan terdeteksi pada LCD
    lcd.backlight();  
    lcd.setCursor(0, 0);  
    lcd.print("Motion Detect !");
    delay(2000); // Delay untuk menampilkan pesan gerakan terdeteksi
  }
  else{
    // Jika tidak ada gerakan yang terdeteksi
    Serial.println("NO motion detect");
    lcd.clear(); // Membersihkan layar LCD
  }
  
  delay(2000); // Delay untuk mengurangi false positives
}

// Fungsi untuk memperbarui tampilan LCD dengan hitungan gerakan
void updateLCD() {
  lcd.setCursor(0, 1);
  lcd.print("Count =  ");
  lcd.print(motioncount);
}
