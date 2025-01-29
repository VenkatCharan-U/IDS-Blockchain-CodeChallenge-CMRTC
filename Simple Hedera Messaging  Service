from datetime import datetime

class HederaMessagingService:
    def __init__(self):
        self.topic_id = "0.0.34567"  # Example topic ID
        self.messages_sent = []
        self.messages_received = []

    def send_message(self, message):
        timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        self.messages_sent.append({"message": message, "timestamp": timestamp})
        # Simulate receiving the message
        self.receive_message(message, timestamp)

    def receive_message(self, message, timestamp):
        self.messages_received.append({"message": message, "timestamp": timestamp})

    def get_sent_messages(self):
        return self.messages_sent

    def get_received_messages(self):
        return self.messages_received

def main():
    service = HederaMessagingService()
    print(f"Topic Created: {service.topic_id}")

    # Send messages
    service.send_message("Hello, Hedera!")
    service.send_message("Learning HCS")
    service.send_message("Message 3")

    # Display sent messages
    print("\nMessages Sent:")
    for i, msg in enumerate(service.get_sent_messages(), 1):
        print(f"{i}. \"{msg['message']}\" at {msg['timestamp']}")

    # Display received messages
    print("\nMessages Received:")
    for i, msg in enumerate(service.get_received_messages(), 1):
        print(f"{i}. \"{msg['message']}\" at {msg['timestamp']}")

if __name__ == "__main__":
    main()
