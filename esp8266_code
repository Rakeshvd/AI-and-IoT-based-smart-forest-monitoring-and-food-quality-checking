#include <ESP8266WiFi.h>
#include <FirebaseArduino.h>
#include <SoftwareSerial.h> 
#include "UbidotsMicroESP8266.h"
#define ID1 "5a93778b642ab64d5d######" 
#define ID2 "5a937896642ab64a34######"
#define ID3 "5a93791e642ab64d53######" 

#define TOKEN  "#####"
Ubidots client(TOKEN);

#define FIREBASE_HOST "#####"
#define FIREBASE_AUTH "#####"
#define WIFI_SSID "****"
#define WIFI_PASSWORD "*****"

int soilmoisturesensor = A0;
int vibrationsensor = D5;
int firesensor = D6;

void setup()
{
  Serial.begin(9600);
  client.wifiConnection(WIFI_SSID,WIFI_PASSWORD);
  pinMode(soilmoisturesensor, INPUT);
  pinMode(vibrationsensor, INPUT);
  pinMode(firesensor, INPUT);
     
  WiFi.begin(WIFI_SSID, WIFI_PASSWORD);
  Serial.print("connecting");
  while (WiFi.status() != WL_CONNECTED) {
    Serial.print(".");
    delay(500);
  }
  Serial.println();
  Serial.print("connected: ");
  Serial.println(WiFi.localIP());

  Firebase.begin(FIREBASE_HOST, FIREBASE_AUTH);
  Serial.println("firebase connected");
  
  Firebase.set("Tree1_Soil_Moisture",1);
  Firebase.set("Tree1_Vibration",1);
  Firebase.set("Tree1_Fire",1);
  Serial.println("firebase set");

 }
 void firebasereconnect(){
Serial.println("Trying to reconnect");
Firebase.begin(FIREBASE_HOST, FIREBASE_AUTH);
}
 
 void loop() {
 if (Firebase.failed()) {
Serial.print("setting /message failed:");
Serial.println(Firebase.error());
firebasereconnect();
return;
delay(100);
}
  
  int sms;
  int smsmapped;
  int vs;
  int fs;
  if(sms != analogRead(A0));
  {
    sms= analogRead(A0);
    smsmapped=map(sms,0,1024,1000,0);
    Firebase.set("Tree1_Soil_Moisture",smsmapped);
    
    client.add(ID1,smsmapped);
        // delay(50);
  }
  if(vs != digitalRead(D5));
  {
    vs= digitalRead(D5);
    Firebase.set("Tree1_Vibration",vs);
    client.add(ID2,vs);
   // delay(50);
  }
  if(fs != digitalRead(D6));
  {
    fs= digitalRead(D6);
    Firebase.set("Tree1_Fire",fs);
    client.add(ID3,fs);
    //delay(50);
  }
  Serial.println(smsmapped);
 // delay(20);
  Serial.println(vs);
//delay(20);
  Serial.println(fs);
  //delay(20);
  client.sendAll(true);
//delay(20);
//delay(50);
}
