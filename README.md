# AI-Powered Image Generation and Object Replacement

This project presents an end-to-end AI pipeline that automates the process of replacing objects in an image based on simple text commands. It pioneers a novel fusion of Natural Language Processing (NLP) and Computer Vision (CV) to create a seamless, prompt-driven editing experience, removing the need for any manual masking or selection.

---

## 🌟 Key Features

- **Prompt-Based Object Replacement**: Simply tell the model what to replace and what to replace it with (e.g., "Replace the bed with a cozy blanket").
- **Fully Automated Masking**: Leverages Meta's Segment Anything Model (SAM), guided by a Large Language Model, to generate precise object masks automatically. No manual effort required.
- **High-Fidelity Image Generation**: Utilizes Stable Diffusion inpainting to generate new objects that are contextually aware, matching the scene's lighting, perspective, and style.
- **Efficient and Accessible**: Built with a quantized language model to ensure the pipeline can run on standard hardware without prohibitive memory requirements.

---

## 🚀 Results

Here is an example of the pipeline in action. The user provided the prompt: *"Replace the bed with a blanket."*

<img width="954" height="332" alt="Image" src="https://github.com/user-attachments/assets/0ef08aca-00c7-47f4-bb90-1b86ab3fe450" />

---

## ⚙️ How It Works: The Architecture

The system operates as a multi-stage pipeline where each component is specialized for a specific task. This modular approach ensures both efficiency and high-quality output.

1.  **Prompt Interpretation (NLP)**
    - A **large-scale quantized language model** receives the user's text prompt.
    - It intelligently parses the command to identify two key entities: the **target object** (to be removed) and the **replacement object** (to be generated).

2.  **Automated Segmentation (CV)**
    - The identified target object is fed as a prompt to the **Segment Anything Model (SAM)**.
    - SAM analyzes the input image and generates a precise, pixel-level mask that perfectly isolates the target object.

3.  **Context-Aware Inpainting (Generative AI)**
    - The original image, the generated mask, and the replacement prompt are passed to the **Stable Diffusion inpainting** model.
    - The model uses the mask as a canvas and the surrounding image for context, generating a new object that seamlessly integrates into the scene.

### Workflow Diagram
```
[User Input: Image + "Replace X with Y"]
             |
             v
[Quantized LLM: Extracts "X" and "Y"]
             |
             v
[SAM: Generates mask for "X" in Image]
             |
             v
[Stable Diffusion: Inpaints mask with "Y"]
             |
             v
[Final Output: Modified Image]
```

---

## 🛠️ Tech Stack

- **Backend**: Python
- **AI/ML Frameworks**: PyTorch, Hugging Face Transformers
- **Core Models**:
    - Language Understanding: A quantized Llama-based model (e.g., QwQ-32B)
    - Segmentation: Segment Anything Model (SAM)
    - Image Generation: Stable Diffusion v1.5 Inpainting
- **Frontend (for demo)**: HTML, CSS, JavaScript

---

## 📦 Setup and Usage

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/ai-object-replacement.git](https://github.com/your-username/ai-object-replacement.git)
    cd ai-object-replacement
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the application:**
    ```bash
    python app.py
    ```
    *(Note: This assumes a `requirements.txt` and `app.py` file exist in the repository.)*

---

## 🔮 Future Work

- **Video Object Replacement**: Extend the pipeline to process video frames for dynamic replacement in motion.
- **Interactive UI**: Develop a more advanced user interface for real-time, conversational editing.
- **Style Preservation**: Implement techniques to better preserve the artistic style of the original image in the generated content.

---

## 📄 License

This project is licensed under the MIT License. See the `LICENSE` file for details.
