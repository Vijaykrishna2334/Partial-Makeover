# Partial-Makeover

# AI Interior Designer using Gemini

This web application allows users to upload a photo of their room, select design preferences, and receive a photorealistic interior design makeover powered by Google's Gemini API.

![AI Interior Designer Demo](https://storage.googleapis.com/aistudio-hosting/project-assets/21151a66-2244-46f9-8692-f044f535d4f3/partial-makeover-demo.gif)

## ✨ Features

-   **Image Upload**: Simple drag-and-drop or file picker interface for uploading room photos.
-   **Deep Customization**: Users can specify:
    -   **Room Type**: Living Room, Kitchen, Bedroom, etc.
    -   **Room Usage**: Select 3-5 functional activities for the space (e.g., "Watching TV," "Reading").
    -   **Room Feel**: Choose a desired mood like 'Cozy', 'Bright', or 'Minimal'.
    -   **Design Style**: Select from 10 distinct interior design aesthetics (e.g., Modern, Scandinavian, Coastal).
    -   **Special Requests**: Add custom text prompts for specific details (e.g., "Include a blue sofa").
-   **AI-Powered Generation**: Leverages the `gemini-2.5-flash-image` model to perform a partial makeover, changing only the non-structural elements of the room.
-   **Interactive Results**:
    -   Displays a clear "Before vs. After" comparison.
    -   Shows a detailed "Design Brief" summarizing the user's choices.
    -   Presents AI-generated design notes explaining the changes.
-   **Iterative Refinement**: Users can provide additional text prompts to refine the generated image without starting over.
-   **Generation History**: Automatically saves every design to the browser's `localStorage` for review.
-   **Prompt Transparency**: Allows users to view the exact, detailed prompt that was sent to the AI.
-   **Download**: Save the final generated high-quality image.

## 🛠️ Tech Stack

-   **Frontend**: React (with Hooks), TypeScript
-   **AI Model**: Google Gemini (`gemini-2.5-flash-image`) via the `@google/genai` SDK
-   **Styling**: Tailwind CSS
-   **Bundling**: The project is self-contained in `index.html` using an `importmap` and Babel Standalone for in-browser JSX/TS transpilation, requiring no local build step.

## 🚀 Getting Started

This project is designed to run directly in the browser without any complex setup or build process.

### Prerequisites

-   A modern web browser (like Chrome, Firefox, or Edge).
-   A Google Gemini API Key. You can get one from [Google AI Studio](https://aistudio.google.com/).

### Installation & Setup

1.  **Clone the repository or download the files:**
    ```bash
    git clone https://github.com/YOUR_USERNAME/ai-interior-designer.git
    cd ai-interior-designer
    ```

2.  **Set up your API Key:**
    The application is configured to read the API key from `process.env.API_KEY`. Since this is a client-side project without a build step, you need to make the key available to the script. The simplest way is to directly replace the placeholder in the code.

    -   Open the `index.html` file.
    -   Find the line `if (!process.env.API_KEY)` and the `new GoogleGenAI(...)` calls.
    -   Replace `process.env.API_KEY` with your actual Gemini API key string.

    For example, change this:
    ```javascript
    const ai = new GoogleGenAI({ apiKey: process.env.API_KEY });
    ```
    To this:
    ```javascript
    const ai = new GoogleGenAI({ apiKey: "YOUR_GEMINI_API_KEY_HERE" });
    ```
    *Note: Remember to do this for all instances where `process.env.API_KEY` is used.*

    **⚠️ Security Warning**: Do not commit your API key directly to a public GitHub repository. This method is suitable for local testing only. For deployment, use a secure method to provide the key.

3.  **Open the application:**
    -   Simply open the `index.html` file in your web browser. You can do this by double-clicking the file or using a simple local server extension like Live Server for VS Code.

## 📂 Project Structure

Even though the final code is bundled into `index.html` for simplicity, the logical structure is as follows:

```
/
├── index.html              # Main entry point, contains all HTML, CSS (via CDN), and JS.
├── App.tsx                 # Main React application component, manages state and UI flow.
├── components/             # Reusable React components.
│   ├── CardSelector.tsx    # Component for selecting design options.
│   └── icons.tsx           # SVG icon components.
├── services/               # Logic for interacting with APIs and local storage.
│   ├── geminiService.ts    # Handles communication with the Gemini API.
│   ├── promptLibrary.ts    # Contains detailed style/mood guides for prompt construction.
│   ├── promptTemplate.ts   # The main template for the AI prompt.
│   └── database.ts         # Manages saving and loading history from localStorage.
├── types.ts                # TypeScript type definitions.
├── constants.ts            # Constant data like options for selectors.
└── readme.md               # This file.
```

## 🤝 Contributing

Contributions are welcome! If you have suggestions for improvements or find a bug, please feel free to open an issue or submit a pull request.

1.  Fork the repository.
2.  Create your feature branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
