Code :-

import subprocess
import platform
from concurrent.futures import ProcessPoolExecutor
from tqdm import tqdm


def is_ip_alive(ip):
    # Define the command based on the operating system
    if platform.system().lower() == "windows":
        # Adjust the timeout value as needed
        command = ["ping", "-n", "1", "-w", "2", ip]
    else:
        # Adjust the timeout value as needed
        command = ["ping", "-c", "1", "-W", "2", ip]

    # Execute the command
    try:
        subprocess.run(command, stdout=subprocess.PIPE,
                       stderr=subprocess.PIPE, check=True)
        return True  # IP is alive
    except subprocess.CalledProcessError:
        return False  # IP is dead


def check_ip_range(ip_range):
    alive_ips = []
    dead_count = 0
    with ProcessPoolExecutor(max_workers=100) as executor, tqdm(total=len(ip_range), desc="Checking IPs") as pbar:
        for ip, result in zip(ip_range, executor.map(is_ip_alive, ip_range)):
            pbar.update(1)
            if result:
                alive_ips.append(ip)
            else:
                dead_count += 1

    alive_count = len(alive_ips)
    print(f"Alive IP count: {alive_count}")
    print(f"Alive IPs: {alive_ips}")
    print(f"Dead IP count: {dead_count}")


def generate_ip_range(start, end):
    common_part = ".".join(start.split(".")[:-1])
    return [f"{common_part}.{i}" for i in range(int(start.split(".")[-1]), int(end.split(".")[-1]) + 1)]


# Example usage: check the range from 192.168.43.1 to 192.168.43.256
start_ip = input("Enter Start IP (192.168.43.1) : ")
end_ip = input("Enter End IP (192.168.43.256) : ")
ip_range = generate_ip_range(start_ip, end_ip)
check_ip_range(ip_range)
