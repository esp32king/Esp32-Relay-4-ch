#include <WiFi.h>
#include <WebServer.h>

// Wi-Fi credentials
const char* ssid = "Your_SSID";
const char* password = "Your_PASSWORD";

// Relay pins
const int relayPins[4] = {23, 22, 21, 19};

// Web server on port 80
WebServer server(80);

// HTML page for relay control
String generateHTML() {
  String html = "<!DOCTYPE html><html><head><title>ESP32 4-Relay Control</title></head><body>";
  html += "<h2>ESP32 4-Relay Control</h2>";

  for (int i = 0; i < 4; i++) {
    html += "<p>Relay " + String(i+1) + ": ";
    html += "<a href='/ON" + String(i) + "'><button style='padding:10px;font-size:18px;'>ON</button></a> ";
    html += "<a href='/OFF" + String(i) + "'><button style='padding:10px;font-size:18px;'>OFF</button></a></p>";
  }

  html += "</body></html>";
  return html;
}

// Handle root
void handleRoot() {
  server.send(200, "text/html", generateHTML());
}

// Turn relay ON
void handleON(int relay) {
  digitalWrite(relayPins[relay], HIGH);
  server.sendHeader("Location", "/");
  server.send(303);
}

// Turn relay OFF
void handleOFF(int relay) {
  digitalWrite(relayPins[relay], LOW);
  server.sendHeader("Location", "/");
  server.send(303);
}

// Generic handlers for each relay
void handleRelayON0() { handleON(0); }
void handleRelayOFF0() { handleOFF(0); }
void handleRelayON1() { handleON(1); }
void handleRelayOFF1() { handleOFF(1); }
void handleRelayON2() { handleON(2); }
void handleRelayOFF2() { handleOFF(2); }
void handleRelayON3() { handleON(3); }
void handleRelayOFF3() { handleOFF(3); }

void setup() {
  Serial.begin(115200);

  // Set relay pins as output
  for (int i = 0; i < 4; i++) {
    pinMode(relayPins[i], OUTPUT);
    digitalWrite(relayPins[i], LOW); // start OFF
  }

  // Connect to Wi-Fi
  WiFi.begin(ssid, password);
  Serial.print("Connecting to Wi-Fi");
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println();
  Serial.print("Connected! ESP32 IP: ");
  Serial.println(WiFi.localIP());

  // Web server routes
  server.on("/", handleRoot);
  server.on("/ON0", handleRelayON0);
  server.on("/OFF0", handleRelayOFF0);
  server.on("/ON1", handleRelayON1);
  server.on("/OFF1", handleRelayOFF1);
  server.on("/ON2", handleRelayON2);
  server.on("/OFF2", handleRelayOFF2);
  server.on("/ON3", handleRelayON3);
  server.on("/OFF3", handleRelayOFF3);

  server.begin();
  Serial.println("HTTP server started");
}

void loop() {
  server.handleClient();
}
