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


---------Game Character System----------
#include <iostream>
#include <vector>
#include <memory>

// Interface Kemampuan
class Ability {
public:
    virtual void use() = 0;
    virtual ~Ability() = default;
};

// Kemampuan Attack
class Attack : public Ability {
public:
    void use() override {
        std::cout << "Using Attack!" << std::endl;
    }
};

// Kemampuan Healing
class Healing : public Ability {
public:
    void use() override {
        std::cout << "Using Healing!" << std::endl;
    }
};

// Kemampuan Defend
class Defend : public Ability {
public:
    void use() override {
        std::cout << "Using Defend!" << std::endl;
    }
};

// Abstraksi karakter
class Character {
protected:
    std::vector<std::shared_ptr<Ability>> abilities;

public:
    virtual void display() = 0;

    void addAbility(std::shared_ptr<Ability> ability) {
        abilities.push_back(ability);
    }

    void useAbilities() {
        for (const auto& ability : abilities) {
            ability->use();
        }
    }

    virtual ~Character() = default;
};

// Player
class Player : public Character {
public:
    void display() override {
        std::cout << "I am a Player" << std::endl;
    }
};

// Enemy
class Enemy : public Character {
public:
    void display() override {
        std::cout << "I am an Enemy" << std::endl;
    }
};

// NPC
class NPC : public Character {
public:
    void display() override {
        std::cout << "I am an NPC" << std::endl;
    }
};
