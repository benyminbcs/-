import socket

def scan_ports(target_ip, start_port, end_port):
    print(f"🔍 در حال اسکن پورت‌های {target_ip} از {start_port} تا {end_port}...\n")
    open_ports = []
    for port in range(start_port, end_port + 1):
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(0.5)
        result = sock.connect_ex((target_ip, port))
        if result == 0:
            print(f"✅ پورت باز: {port}")
            open_ports.append(port)
        sock.close()
    if not open_ports:
        print("❌ هیچ پورتی باز نیست.")
    return open_ports

# اجرای برنامه
if __name__ == "__main__":
    target = input("🔢 آدرس آی‌پی هدف (مثلاً 127.0.0.1): ")
    start = int(input("⬅️ شروع پورت: "))
    end = int(input("➡️ پایان پورت: "))
    scan_ports(target, start, end)
