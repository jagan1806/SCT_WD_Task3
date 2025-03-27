# Task 03: Interactive Quiz Game Application

## Project Overview

An interactive multiple-choice quiz game that displays questions, collects answers, and provides a score at the end. The application supports multiple question types including single choice, multiple choice, and fill-in-the-blank formats.

## Features

- **Multiple Question Types**
  - Single-choice (radio button style)
  - Multiple-choice (checkbox style)
  - Fill-in-the-blank (text input)

- **Interactive UI Elements**
  - Progress bar to track quiz completion
  - Navigation between questions
  - Visual feedback for answer selection
  - Timer to track quiz duration

- **Scoring System**
  - Points-based scoring with different weights per question type
  - Detailed results summary
  - Percentage calculation
  - Performance-based feedback messages

- **User Experience**
  - Welcoming start screen with instructions
  - Clean, modern interface with subtle animations
  - Responsive design for all device sizes
  - Clear visual indicators for correct/incorrect answers

## Technologies Used

- HTML5 for structure
- CSS3 for styling (grid, flexbox, animations)
- Vanilla JavaScript for quiz logic
- Local storage for potential quiz data persistence
- No external dependencies or frameworks

## Implementation Details

### Question Types Handling

The application handles different question types through a unified rendering system:

```javascript
function loadQuestion(index) {
    const question = quizData[index];
    
    // Clear previous options
    answerOptions.innerHTML = '';
    
    // Add appropriate class for question type
    answerOptions.className = 'answer-options';
    
    // Create options based on question type
    if (question.type === 'single-choice') {
        // Render single choice options
    } else if (question.type === 'multi-choice') {
        // Render multiple choice options
    } else if (question.type === 'fill-blank') {
        // Render fill in the blank input
    }
}
```

### Score Calculation

Scores are calculated based on question type and correctness:

```javascript
function calculateScore() {
    score = 0;
    
    quizData.forEach((question, index) => {
        const userAnswer = userAnswers[index];
        
        if (question.type === 'single-choice') {
            if (userAnswer === question.correctAnswer) {
                score += question.points;
            }
        } else if (question.type === 'multi-choice') {
            // Compare arrays for exact match
        } else if (question.type === 'fill-blank') {
            // Handle case sensitivity options
        }
    });
    
    return score;
}
```

### Results Display

The application provides detailed feedback on quiz performance:

```javascript
function finishQuiz() {
    // Calculate final score and percentage
    const finalScore = calculateScore();
    const maxScore = quizData.reduce((total, q) => total + q.points, 0);
    const percentage = Math.round((finalScore / maxScore) * 100);
    
    // Determine feedback message based on score
    if (percentage >= 90) {
        scoreMessage.textContent = "Excellent! You're a true genius!";
    } else if (percentage >= 70) {
        scoreMessage.textContent = "Great job! You know your stuff!";
    } else if (percentage >= 50) {
        scoreMessage.textContent = "Good effort! You passed the quiz.";
    } else {
        scoreMessage.textContent = "Keep practicing! You'll do better next time.";
    }
    
    // Create detailed question summary
    createResultsSummary();
}
```

## Quiz Data Structure

The quiz uses a flexible data structure that supports all question types:

```javascript
const quizData = [
    {
        type: 'single-choice',
        question: 'Which planet is known as the "Red Planet"?',
        options: ['Venus', 'Mars', 'Jupiter', 'Saturn'],
        correctAnswer: 1, // Index of the correct answer
        points: 10
    },
    {
        type: 'multi-choice',
        question: 'Which of the following are programming languages?',
        options: ['Python', 'Cobra', 'Java', 'Latte'],
        correctAnswer: [0, 2], // Indices of correct answers
        points: 15
    },
    {
        type: 'fill-blank',
        question: 'The capital of France is _______.',
        correctAnswer: 'Paris',
        points: 10,
        caseSensitive: false
    }
    // More questions...
];
```

## How to Use

1. Clone this repository
2. Open `index.html` in any modern web browser
3. Click "Start Quiz" to begin
4. Answer each question by selecting options or typing answers
5. Navigate using the Previous and Next buttons
6. Submit your answers to see your results
7. Click "Take Quiz Again" to restart

## Customization

The quiz can be easily customized by modifying the `quizData` array in the JavaScript file. You can:
- Add new questions of any supported type
- Change correct answers
- Adjust point values
- Modify feedback messages

## Future Enhancements

- Add more question types (matching, ordering, etc.)
- Implement question categories
- Add difficulty levels
- Create a question editor interface
- Support for importing/exporting quiz data
- Add timed questions with automatic progression

## Screenshots


## License

This project is part of the SkillCraft Technology internship program.
