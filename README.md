# AquaSentinel-
ESP32-based optical water monitoring and plastic contamination treatment prototype.
void loop() {
  int sensorValue = digitalRead(LDR_PIN);

  Serial.print("LDR Reading: ");
  Serial.println(sensorValue);

  if (sensorValue == PARTICLE_SIGNAL) {
    // Possible particle detected
    digitalWrite(GREEN_LED, LOW);
    digitalWrite(YELLOW_LED, HIGH);
    digitalWrite(RED_LED, LOW);

    Serial.println("Possible particle detected.");
    Serial.println("Routing water to filtration.");

    relayON();

  } else {
    // No configured optical-change signal
    digitalWrite(GREEN_LED, HIGH);
    digitalWrite(YELLOW_LED, LOW);
    digitalWrite(RED_LED, LOW);

    relayOFF();

    Serial.println("No configured optical-change signal detected.");
    Serial.println("Microplastic presence is not confirmed.");
  }

  delay(500);
}
