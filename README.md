import webbrowser
from time import sleep

def display_intro():
    print("\n" + "="*50)
    print(" " * 15 + "AI TOOLS PRESENTATION")
    print("="*50)
    print("\nWelcome to this interactive presentation of cutting-edge AI tools!")
    print("I'll introduce you to several powerful AI platforms across different categories.")
    sleep(2)

def display_categories():
    categories = {
        "1": "Chat/Language AI",
        "2": "Image Generation",
        "3": "Video Generation",
        "4": "Multimedia Creative Tools"
    }
    
    print("\n" + "-"*50)
    print("MAIN CATEGORIES:")
    for num, name in categories.items():
        print(f"{num}. {name}")
    print("-"*50)

def get_user_choice():
    while True:
        choice = input("\nEnter a category number to explore (1-4) or 'q' to quit: ")
        if choice.lower() == 'q':
            return None
        if choice in ['1', '2', '3', '4']:
            return choice
        print("Invalid input. Please try again.")

def show_tools(category):
    tools = {
        "1": [
            ("DeepSeek Chat", "https://chat.deepseek.com/", "Advanced AI chat assistant"),
            ("ChatGPT", "https://chatgpt.com/", "OpenAI's conversational AI"),
            ("Kling AI", "https://pro.klingai.com/global/dev", "Video generation from text")
        ],
        "2": [
            ("Midjourney", "https://www.midjourney.com/home", "AI art generation"),
            ("Leonardo AI", "https://leonardo.ai/", "Creative image generation"),
            ("DreamStudio", "https://beta.dreamstudio.ai/generate", "Stable Diffusion web interface")
        ],
        "3": [
            ("Runway ML", "https://runwayml.com/", "AI video editing and generation"),
            ("Hailuo AI", "https://hailuoai.video/", "AI video creation tools"),
            ("Kling AI", "https://pro.klingai.com/global/dev", "Text-to-video generation")
        ],
        "4": [
            ("Runway ML", "https://runwayml.com/", "Multimedia creative suite"),
            ("Leonardo AI", "https://leonardo.ai/", "Image and design tools"),
            ("DreamStudio", "https://beta.dreamstudio.ai/generate", "Creative image generation")
        ]
    }
    
    print("\n" + "="*50)
    print(f"TOOLS IN THIS CATEGORY:")
    for idx, (name, url, desc) in enumerate(tools[category], 1):
        print(f"\n{idx}. {name}")
        print(f"   {desc}")
        print(f"   URL: {url}")
    print("="*50)
    
    while True:
        choice = input("\nEnter a tool number to open in browser, 'b' to go back, or 'q' to quit: ")
        if choice.lower() == 'q':
            return False
        if choice.lower() == 'b':
            return True
        if choice.isdigit() and 1 <= int(choice) <= len(tools[category]):
            webbrowser.open(tools[category][int(choice)-1][1])
            print(f"Opening {tools[category][int(choice)-1][0]} in your browser...")
        else:
            print("Invalid input. Please try again.")

def main():
    display_intro()
    
    while True:
        display_categories()
        choice = get_user_choice()
        
        if not choice:
            break
            
        continue_browsing = show_tools(choice)
        if not continue_browsing:
            break
    
    print("\nThank you for exploring AI tools with us!")
    print("We hope you discovered some powerful resources for your projects.")
    print("Have a great day!\n")

if __name__ == "__main__":
    main()
