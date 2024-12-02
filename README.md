from collections import Counter

def analyze_logs(file_path):
    with open(file_path, 'r') as f:
        logs = f.readlines()

    # Count 404 errors
    errors = [log for log in logs if '404' in log]
    print(f"Total 404 Errors: {len(errors)}")

    # Most requested pages
    pages = [line.split()[6] for line in logs]
    most_requested = Counter(pages).most_common(5)
    print("Most Requested Pages:")
    for page, count in most_requested:
        print(f"{page}: {count} requests")

    # Most frequent IPs
    ips = [line.split()[0] for line in logs]
    most_frequent_ips = Counter(ips).most_common(5)
    print("Most Frequent IPs:")
    for ip, count in most_frequent_ips:
        print(f"{ip}: {count} requests")

if __name__ == "__main__":
    analyze_logs("access.log")
