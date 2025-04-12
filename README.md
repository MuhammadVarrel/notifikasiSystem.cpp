#include <iostream>
#include <memory>
#include <vector>

// Interface
class Notification {
public:
    virtual void send(const std::string& message) = 0;
    virtual ~Notification() = default;
};

// Implementasi Email
class EmailNotification : public Notification {
public:
    void send(const std::string& message) override {
        std::cout << "Sending Email: " << message << std::endl;
    }
};

// Implementasi SMS
class SMSNotification : public Notification {
public:
    void send(const std::string& message) override {
        std::cout << "Sending SMS: " << message << std::endl;
    }
};

// Implementasi Push Notification
class PushNotification : public Notification {
public:
    void send(const std::string& message) override {
        std::cout << "Sending Push Notification: " << message << std::endl;
    }
};

// Fungsi utama
void sendNotification(Notification* notifier, const std::string& message) {
    notifier->send(message);
}
