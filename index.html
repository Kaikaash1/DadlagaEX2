#include <Arduino.h>
#include <WiFiMulti.h>
#include <WebServer.h>


#define WIFI_SSID "VIOT"
#define WIFI_PASSWORD "qwer123@"

WiFiMulti wifiMulti;

WebServer server(80);

// Motor control pin (PWM capable)
const int motorPin = 16; // Change to your motor PWM pin
int motorSpeed = 0; // 0-255

// HTML content for the web page
const char* htmlContent = R"rawliteral(
<!DOCTYPE HTML><html>
<head>
  <title>ESP32 Motor Speed Control</title>
  <style>
    body { font-family: Arial, sans-serif; text-align: center; }
    h1 { color: #0F3376; padding: 2vh; }
    .slider { width: 300px; }
    .value { font-size: 1.2rem; color: #333; }
  </style>
</head>
<body>
  <h1>ESP32 Motor Speed Control</h1>
  <p>Set motor speed:</p>
  <input type="range" min="0" max="255" value="0" class="slider" id="speedSlider" oninput="updateValue(this.value)">
  <span class="value" id="speedValue">0</span>
  <script>
    function updateValue(val) {
      document.getElementById('speedValue').innerText = val;
      fetch('/setSpeed?value=' + val);
    }
  </script>
</body>
</html>
)rawliteral";

// Function to handle the root path
void handleRoot() {
  server.send(200, "text/html", htmlContent);
}

// Function to handle speed setting
void handleSetSpeed() {
  if (server.hasArg("value")) {
    motorSpeed = server.arg("value").toInt();
    ledcWrite(0, motorSpeed); // Channel 0
  }
  server.send(200, "text/plain", String(motorSpeed));
}


void setup() {
  Serial.begin(115200);
  // Setup PWM for motor
  ledcSetup(0, 5000, 8); // Channel 0, 5kHz, 8-bit resolution
  ledcAttachPin(motorPin, 0);
  ledcWrite(0, 0); // Start with motor off


  // Add WiFi network(s)
  wifiMulti.addAP(WIFI_SSID, WIFI_PASSWORD);
  Serial.print("Connecting to WiFi");
  while (wifiMulti.run() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println("");
  Serial.println("WiFi connected.");
  Serial.print("IP address: ");
  Serial.println(WiFi.localIP());

  // Route for root / web page
  server.on("/", handleRoot);
  // Route to set motor speed
  server.on("/setSpeed", handleSetSpeed);

  // Start server
  server.begin();
  Serial.println("HTTP server started.");
}

void loop() {
  server.handleClient();
}
