# website_checker.py
import requests.

def check_website(url):
    try:
        response = requests.get(url, timeout=5)
        if response.status_code == 200:
            print(f"✅ {url} در دسترس است.")
        else:
            print(f"⚠️ {url} پاسخ داد، ولی وضعیت: {response.status_code}")
    except requests.exceptions.RequestException:
        print(f"❌ {url} در دسترس نیست.")

def main():
    print("🌐 بررسی وضعیت وبسایت")
    while True:
        url = input("آدرس وبسایت (مثال: https://google.com) یا 'exit' برای خروج: ")
        if url.lower() == "exit":
            print("👋 خداحافظ!")
            break
        if not url.startswith("http"):
            url = "https://" + url
        check_website(url)

if __name__ == "__main__":
    main()
