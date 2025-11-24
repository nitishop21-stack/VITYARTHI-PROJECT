**PROJECT TITLE: ROCK, PAPER, SCISSORS GAME USING PYTHON** 

**Overview of the Project**

This project creates a classic **Rock, Paper, Scissors** game for the command-line interface (CLI). It focuses on delivering a simple yet engaging user experience by incorporating essential game features, robust input handling, and clear, color-coded terminal output. The project is an application of concepts learned in the VITYARTHI course. 

**Problem Statement** 

Traditional command-line games often suffer from poor user experience due to unstructured output and rigid input requirements, making them tedious for quick, casual play. 

The main problems addressed are:

- **Lack of Feedback:** No immediate visual distinction between a win, loss, or tie. 
- **Input Inflexibility:** Games often require exact spelling, leading to invalid input errors for simple abbreviations (e.g., using "r" instead of "rock"). 
- **Poor Score Tracking:** Lack of a clearly displayed score board to track progress across multiple rounds. 

**Solution (Project Goal)** 

The Rock, Paper, Scissors Console Game addresses these issues by providing a fully tracked and visually enhanced experience: 

- **Robust Input Handling:** The custom input Handler function allows for **flexible and partial user inputs** (e.g., "roc" or "p" are correctly mapped). 
- **Colorized Results:** **ANSI escape codes** (GREEN, RED, YELLOW) are used to immediately color-coded the results for wins, losses, and ties, improving visual clarity. 
- **Score Board:** A dedicated display scores function presents the 

  current win/loss/tie tally clearly after every round. 

**Features of the Project** 

The project focuses on enhancing the user experience in a console environment. 

- **Error Reduction and Highly Accurate**  
- **Colorized Results** (ANSI Codes)  
- **Green** for User Win  
- **Red** for Computer Win  
- **Yellow** for Tie  
- **Automated Features**: Score tracking, round incrementing, and computer move generation. 
- **Robust Input Handling** : Accepts partial strings like 'sci' for 'scissors'. 

**Tools Used** 

**Tool/Technology**  **Role** ![](Aspose.Words.f78c36d2-6302-462f-86de-8ec28b0f1cbd.001.png)![](Aspose.Words.f78c36d2-6302-462f-86de-8ec28b0f1cbd.002.png)

**Python**  Primary programming language **Random Module**  Generates the computer's choice 

**Tool/Technology**  **Role** ![](Aspose.Words.f78c36d2-6302-462f-86de-8ec28b0f1cbd.003.png)![](Aspose.Words.f78c36d2-6302-462f-86de-8ec28b0f1cbd.004.png)

**ANSI Escape Codes** Provides colorization and UI feedback 

**Steps to Install and Run** 

This is a single-file application requiring only Python 3. 

1. **Download the file** attached: Ensure the Python code is saved as rck.py. 
1. **Open Terminal/Command Prompt:** Navigate to the directory where you saved rck.py. 
1. **Run the file:** Execute the script using the Python interpreter:

Bash 

python rck.py 

4. **Play:** Enter your choice ('rock', 'paper', 'scissors', or '0' to exit) when prompted. 

**Scope of the Project** 

The scope of this project is limited to the console environment, serving as a functional demonstration of core programming concepts.

- **Functional Goal:** To provide a simple, continuous **single-user** gaming experience. 
- **Educational Goal:** To showcase **Modular Programming** (using functions like win\_dec and display scores) and techniques for **enhanced UX** in CLI applications using colour codes22. 

Potential Future Developments  

- **Best-of-N Format:** Implement a structure to play for a predefined number of rounds (e.g., best-of-5). 
- **User Profiles:** Save and load user scores to a file (CSV or JSON) to track long-term performance. 
- **Error Handling:** Use a more structured approach to catch and handle all potential user input errors. 

**Target Users** 

This project is primarily an educational and introductory tool demonstrating Python programming.

- **VITYARTHI Course Students:** To reinforce concepts of basic game logic, state management, and user input handling. 
- **Beginner Python Developers:** To study clean function separation and enhancing terminal output.
- **Individual Users:** For quick, casual play against the computer.
