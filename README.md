# scanning-open-ports-on-a-target-system.
#Use this responsibly. Always ensure you have permission before scanning any system that you don't own.
import socket

# Function to scan ports
def scan_ports(target, ports):
    print(f"Scanning {target} for open ports...\n")
    for port in ports:
        try:
            # Create a socket
            with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
                s.settimeout(1)  # Timeout for connection
                if s.connect_ex((target, port)) == 0:
                    print(f"Port {port} is open.")
                else:
                    print(f"Port {port} is closed.")
        except Exception as e:
            print(f"Error scanning port {port}: {e}")

# Target and ports to scan
target_host = "127.0.0.1"  # Replace with target IP
ports_to_scan = [22, 80, 443, 8080]  # Common ports to scan

# Run the scanner
scan_ports(target_host, ports_to_scan)
