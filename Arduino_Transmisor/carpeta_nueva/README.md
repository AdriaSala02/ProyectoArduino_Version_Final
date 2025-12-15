#pragma once
#include <Arduino.h>

// ===== MOCK SoftwareSerial =====
class MockSerial {
public:
  uint8_t buffer[64];
  int idx = 0;

  void write(uint8_t b) { buffer[idx++] = b; }
  void write(const uint8_t *b, size_t len) {
    for (size_t i = 0; i < len; i++) buffer[idx++] = b[i];
  }
  void reset() { idx = 0; }
};

extern MockSerial mockSerial;

// ===== MOCK pulseIn =====
long mockPulseValue = 0;
long pulseIn(uint8_t pin, uint8_t state, unsigned long timeout) {
  return mockPulseValue;
}
