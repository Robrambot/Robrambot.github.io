<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>All Course Practice Exercises</title>

  <style>
    :root {
      --primary: #2563eb;
      --primary-dark: #1e40af;
      --secondary: #14b8a6;
      --bg: #f8fafc;
      --card: #ffffff;
      --text: #0f172a;
      --muted: #64748b;
      --correct: #16a34a;
      --incorrect: #dc2626;
      --border: #e2e8f0;
      --shadow: 0 20px 40px rgba(15, 23, 42, 0.08);
      --radius: 22px;
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: "Inter", "Segoe UI", Arial, sans-serif;
      background:
        radial-gradient(circle at top left, #dbeafe 0, transparent 35%),
        radial-gradient(circle at bottom right, #ccfbf1 0, transparent 35%),
        var(--bg);
      color: var(--text);
      min-height: 100vh;
    }

    header {
      padding: 28px 20px;
      text-align: center;
    }

    header h1 {
      margin: 0;
      font-size: clamp(2rem, 4vw, 3.2rem);
      color: var(--primary-dark);
      letter-spacing: -0.04em;
    }

    header p {
      margin-top: 12px;
      color: var(--muted);
      font-size: 1.05rem;
    }

    main {
      width: min(1050px, 94%);
      margin: 0 auto 60px;
    }

    .card {
      background: rgba(255, 255, 255, 0.92);
      backdrop-filter: blur(12px);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding: 28px;
      margin-bottom: 24px;
    }

    .start-card {
      text-align: center;
      padding: 42px 28px;
    }

    .badge {
      display: inline-block;
      background: #eff6ff;
      color: var(--primary-dark);
      border: 1px solid #bfdbfe;
      padding: 8px 14px;
      border-radius: 999px;
      font-weight: 700;
      font-size: 0.9rem;
      margin-bottom: 16px;
    }

    .btn {
      border: none;
      cursor: pointer;
      border-radius: 14px;
      padding: 13px 20px;
      font-weight: 800;
      font-size: 1rem;
      transition: transform 0.15s ease, box-shadow 0.15s ease, background 0.15s ease;
    }

    .btn:hover {
      transform: translateY(-1px);
      box-shadow: 0 10px 22px rgba(37, 99, 235, 0.22);
    }

    .btn-primary {
      background: linear-gradient(135deg, var(--primary), var(--secondary));
      color: white;
    }

    .btn-secondary {
      background: #e2e8f0;
      color: var(--text);
    }

    .top-bar {
      display: flex;
      justify-content: space-between;
      gap: 16px;
      align-items: center;
      margin-bottom: 18px;
      flex-wrap: wrap;
    }

    .progress-wrap {
      flex: 1;
      min-width: 220px;
    }

    .progress-info {
      display: flex;
      justify-content: space-between;
      color: var(--muted);
      font-weight: 700;
      margin-bottom: 8px;
      font-size: 0.95rem;
    }

    .progress-track {
      width: 100%;
      height: 12px;
      background: #e2e8f0;
      border-radius: 999px;
      overflow: hidden;
    }

    .progress-fill {
      height: 100%;
      width: 0%;
      background: linear-gradient(90deg, var(--primary), var(--secondary));
      transition: width 0.3s ease;
    }

    .question-title {
      color: var(--primary-dark);
      font-size: 1rem;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      font-weight: 900;
      margin-bottom: 8px;
    }

    .question-text {
      font-size: 1.22rem;
      line-height: 1.6;
      margin-bottom: 22px;
    }

    .math {
      display: inline-flex;
      align-items: center;
      font-family: "Cambria Math", "Times New Roman", serif;
      font-size: 1.1em;
      background: #f1f5f9;
      padding: 3px 7px;
      border-radius: 8px;
      white-space: nowrap;
      vertical-align: middle;
    }

    .math mjx-container {
      margin: 0 !important;
    }

    .options {
      display: grid;
      gap: 12px;
    }

    .option {
      border: 1px solid var(--border);
      background: #ffffff;
      padding: 14px 16px;
      border-radius: 16px;
      cursor: pointer;
      display: flex;
      gap: 12px;
      align-items: flex-start;
      transition: border 0.15s ease, background 0.15s ease, transform 0.15s ease;
    }

    .option:hover {
      border-color: var(--primary);
      background: #f8fafc;
      transform: translateY(-1px);
    }

    .option input {
      margin-top: 4px;
    }

    .option.correct {
      border-color: var(--correct);
      background: #ecfdf5;
    }

    .option.incorrect {
      border-color: var(--incorrect);
      background: #fef2f2;
    }

    .feedback {
      margin-top: 18px;
      padding: 16px;
      border-radius: 16px;
      display: none;
      line-height: 1.5;
    }

    .feedback.correct {
      display: block;
      background: #ecfdf5;
      color: #14532d;
      border: 1px solid #bbf7d0;
    }

    .feedback.incorrect {
      display: block;
      background: #fef2f2;
      color: #7f1d1d;
      border: 1px solid #fecaca;
    }

    .actions {
      display: flex;
      justify-content: space-between;
      gap: 12px;
      margin-top: 22px;
      flex-wrap: wrap;
    }

    .hidden {
      display: none;
    }

    .result-score {
      font-size: 3rem;
      color: var(--primary-dark);
      margin: 10px 0;
      font-weight: 900;
    }

    .review-item {
      border-top: 1px solid var(--border);
      padding: 16px 0;
    }

    .placeholder-note {
      border: 2px dashed #94a3b8;
      border-radius: 16px;
      padding: 18px;
      background: #f8fafc;
      color: var(--muted);
      margin-bottom: 18px;
      font-weight: 700;
    }

    @media (max-width: 700px) {
      .card {
        padding: 22px;
      }

      .question-text {
        font-size: 1.05rem;
      }
    }
  </style>
</head>

<body>
  <header>
    <h1>All Course Practice Exercises</h1>
    <p>Interactive practice for linear, quadratic, polynomial, and modeling topics.</p>
  </header>

  <main>
    <section id="startScreen" class="card start-card">
      <span class="badge">Mathematical Modeling Practice</span>
      <h2>Practice with mixed exercises from the course</h2>
      <p>
        You will answer one question at a time. After each answer, the correct option
        and a short explanation will appear.
      </p>
      <button class="btn btn-primary" onclick="startPractice()">Start Practice</button>
    </section>

    <section id="quizScreen" class="card hidden">
      <div class="top-bar">
        <div class="progress-wrap">
          <div class="progress-info">
            <span id="questionCounter">Question 1 of 19</span>
            <span id="scoreCounter">Score: 0</span>
          </div>
          <div class="progress-track">
            <div id="progressFill" class="progress-fill"></div>
          </div>
        </div>
      </div>

      <div id="questionArea"></div>

      <div class="actions">
        <button id="checkBtn" class="btn btn-primary" onclick="checkAnswer()">Check Answer</button>
        <button id="nextBtn" class="btn btn-secondary hidden" onclick="nextQuestion()">Next Question</button>
      </div>
    </section>

    <section id="resultScreen" class="card hidden">
      <span class="badge">Practice Completed</span>
      <h2>Your Results</h2>
      <div id="finalScore" class="result-score"></div>
      <p id="finalMessage"></p>

      <div class="actions">
        <button class="btn btn-primary" onclick="restartPractice()">Practice Again</button>
      </div>

      <h3>Review</h3>
      <div id="reviewArea"></div>
    </section>
  </main>

  <script>
    const questionBank = [
      {
        topic: "Linear Inequalities",
        question: `Solve the inequality: $-4 < \\frac{8 - 2x}{2} \\leq 6$`,
        options: [
          "$[-2, 8)$",
          "$(-2, 8]$",
          "$[-8, 2)$",
          "$(-\\infty, 8)$"
        ],
        answer: 0,
        explanation: "Multiply by 2, subtract 8, and divide by -2. Remember to flip the inequalities when dividing by a negative number."
      },
      {
        topic: "Linear Equations",
        question: `Solve: $3[2x - (x - 4)] + 2(x - 5) = 4[x + 3(x - 2)] - 7$`,
        options: [
          "$x = 2$",
          "$x = 3$",
          "$x = -3$",
          "$x = 6$"
        ],
        answer: 1,
        explanation: "Simplify brackets first, then combine like terms. The solution is $x = 3$."
      },
      {
        topic: "Linear Equations",
        question: `Solve: $5[2y - (y + 1)] - 3(y - 4) = 2[3y - (y - 2)] + 7$`,
        options: [
          "y = 0",
          "y = 1",
          "y = -2",
          "y = 4"
        ],
        answer: 2,
        explanation: "Distribute carefully through brackets and parentheses. After simplifying, y = 0."
      },
      {
        topic: "Domain and Range",
        multiPart: true,
        graphPlaceholder: '<img src="domain_range1.png" alt="Domain and Range graph" class="graph-image">',
        question: "Use the graph to select the correct domain and range.",
        parts: [
          {
            label: "Part A: Select the correct domain.",
            options: [
              "Option A: (-inf,-4] U (-2, 11]",
              "Option B: (-inf,-4) U (-2, 6] U [6, 11]",
              "Option C: (-inf,inf)",
              "Option D: [-4, -2] U [6, 11]"
            ],
            answer: 0
          },
          {
            label: "Part B: Select the correct range.",
            options: [
              "Option A: (-inf,-4] U (-2, 11]",
              "Option B: (-5,0] U [1,2) U [3, inf)",
              "Option C: (-inf,inf)",
              "Option D: (-5,0) U (1,2) U (3, inf)"
            ],
            answer: 1
          }
        ],
        explanation: "The domain is the set of possible x-values. The range is the set of possible y-values."
      },
      {
        topic: "Domain and Range",
        multiPart: true,
        graphPlaceholder: '<img src="domain_range2.png" alt="Domain and Range graph" class="graph-image">',
        question: "Use the graph to select the correct domain and range.",
        parts: [
          {
            label: "Part A: Select the correct domain.",
            options: [
              "Option A: (-inf,-4] U (-2, 11]",
              "Option B: (-5,0] U [1,2) U [3, inf)",
              "Option C: (-inf,inf)",
              "Option D: (-5,0) U (1,2) U (3, inf)"
            ],
            answer: 2
          },
          {
            label: "Part B: Select the correct range.",
            options: [
              "Option A: [-4,2]",
              "Option B: (-5,0] U [1,2) U [3, inf)",
              "Option C: (-inf,inf)",
              "Option D: (-5,0) U (1,2) U (3, inf)"
            ],
            answer: 0
          }
        ],
        explanation: "Check the leftmost and rightmost x-values for the domain, and the lowest and highest y-values for the range."
      },
            {
        topic: "Linear Functions",
        question: `A line passes through <span class="math">(-2, 5)</span> and has slope <span class="math">-3</span>. What is the point-slope form?`,
        options: [
          "y - 5 = -3(x + 2)",
          "y + 5 = -3(x - 2)",
          "y - 5 = 3(x + 2)",
          "y + 5 = 3(x - 2)"
        ],
        answer: 0,
        explanation: "Use point-slope form: y - y_1 = m(x - x_1). Substitute (-2,5) and m = -3."
      },
      {
        topic: "Linear Functions",
        question: `Find the slope of the line passing through <span class="math">(-4, 2)</span> and <span class="math">(2, 8)</span>.`,
        options: [
          "1",
          "2",
          "-1",
          "3"
        ],
        answer: 0,
        explanation: "Slope = (8 - 2) / (2 - (-4)) = 6/6 = 1."
      },
      {
        topic: "Polynomial Functions",
        question: `
          Select the graph that best represents the polynomial 
          <span class="math">f(x) = -x^4 + 6x^3 - 8x^2 - 6x + 9</span>.

          <div style="margin-top:20px;">
            <div style="margin:10px;">
              <h4 style="margin:0 0 8px;">Graph A</h4>
              <img src="poly_1.png" style="width:100%; max-width:400px; border-radius:12px;">
            </div>
            <div style="margin:10px;">
              <h4 style="margin:0 0 8px;">Graph B</h4>
              <img src="poly_2.png" style="width:100%; max-width:400px; border-radius:12px;">
            </div>
            <div style="margin:10px;">
              <h4 style="margin:0 0 8px;">Graph C</h4>
              <img src="poly_3.png" style="width:100%; max-width:400px; border-radius:12px;">
            </div>
          </div>
        `,
        options: [
          "Graph A",
          "Graph B",
          "Graph C"
        ],
        answer: 1,
        explanation: "Even degree and negative leading coefficient -> both ends down. Compare intercepts and turning points."
      },
      {
        topic: "Polynomial Functions",
        question: `
          From the graph, select the polynomial in factored form.

          <div style="margin-top:20px;">
            <img src="poly_fact.png" style="width:100%; max-width:500px; border-radius:12px;">
          </div>
        `,
        options: [
          "f(x) = (1/6)(x + 3)(x - 2)(x + 1)",
          "f(x) = (1/6)(x - 3)(x + 2)(x - 1)",
          "f(x) = (x + 3)(x - 2)(x + 1)",
          "f(x) = -(1/6)(x + 3)(x - 2)(x + 1)"
        ],
        answer: 0,
        explanation: "The graph crosses at x = -3, -1, and 2. The scaling factor is 1/6. y intercept is -1"
      },
      {
        topic: "Quadratic Functions",
        question: `Solve <span class="math">x^2 - 7x + 12 = 0</span>.`,
        options: [
          "x = 3, 4",
          "x = -3, -4",
          "x = 2, 6",
          "x = -2, -6"
        ],
        answer: 0,
        explanation: "Factor: (x - 3)(x - 4) = 0."
      },
      {
        topic: "Quadratic Functions",
        question: `For <span class="math">f(x) = -2(x - 3)^2 + 5</span>, what is the vertex?`,
        options: [
          "(3, 5)",
          "(-3, 5)",
          "(3, -5)",
          "(0, 5)"
        ],
        answer: 0,
        explanation: "Vertex form: (h,k). Here h = 3 and k = 5."
      },
      {
        topic: "Cubic Functions",
        question: `Factor <span class="math">f(x) = x^3 - 4x^2 - x + 4</span>.`,
        options: [
          "(x - 4)(x - 1)(x + 1)",
          "(x - 2)(x - 2)(x + 1)",
          "(x - 4)(x + 1)^2",
          "(x - 1)(x + 4)(x - 1)"
        ],
        answer: 0,
        explanation: "Group terms: x^2(x - 4) - 1(x - 4). Factor: (x - 4)(x^2 - 1)."
      },
      {
        topic: "Cubic Functions",
        question: `Given that <span class="math">x = -1</span> is a root of <span class="math">2x^3 - 3x^2 - 8x - 3</span>, what is the factorization?`,
        options: [
          "(x + 1)(2x + 1)(x - 3)",
          "(x - 1)(2x + 1)(x + 3)",
          "(x + 1)(x + 3)(2x - 1)",
          "(x - 1)(x + 1)(2x - 3)"
        ],
        answer: 0,
        explanation: "Use synthetic division with -1, then factor the quadratic."
      },
            {
        topic: "Systems of Linear Equations",
        question: `Solve the system: 
        <span class="math">x + y = 11</span> and <span class="math">y = 2x - 1</span>.`,
        options: [
          "(4, 7)",
          "(5, 6)",
          "(3, 8)",
          "(6, 5)"
        ],
        answer: 0,
        explanation: "Substitute y = 2x - 1 into x + y = 11 -> x + 2x - 1 = 11 -> 3x = 12 -> x = 4, y = 7."
      },
      {
        topic: "Systems of Linear Equations",
        question: `Solve the system: 
        <span class="math">3x + 2y = 16</span> and <span class="math">x - y = 1</span>.`,
        options: [
          "(18/5, 13/5)",
          "(4, 2)",
          "(5, 3)",
          "(3, 1)"
        ],
        answer: 0,
        explanation: "From x - y = 1 -> x = y + 1. Substitute into first equation and solve."
      },
      {
        topic: "Remainder Theorem",
        question: `Find <span class="math">k</span> such that the remainder is 10 when 
        <span class="math">P(x) = kx^3 + 2x^2 - 5x + 1</span> is divided by <span class="math">x - 2</span>.`,
        options: [
          "3/8",
          "11/8",
          "2",
          "-3/8"
        ],
        answer: 1,
        explanation: "Use P(2) = 10 -> 8k + 8 - 10 + 1 = 10 -> 8k - 1 = 10 -> k = 11/8."
      },
      {
        topic: "Application Problems",
        question: `A gym charges a $15 registration fee and $8 per class. 
        How many classes can be taken with $63?`,
        options: [
          "6",
          "5",
          "7",
          "8"
        ],
        answer: 0,
        explanation: "63 = 15 + 8x -> 48 = 8x -> x = 6."
      },
      {
        topic: "Application Problems",
        question: `The height of a ball is given by 
        <span class="math">h(t) = -16t^2 + 96t</span>. 
        When does it reach maximum height?`,
        options: [
          "3 seconds",
          "6 seconds",
          "2 seconds",
          "4 seconds"
        ],
        answer: 0,
        explanation: "Vertex formula: t = -b / (2a) = -96 / (2 * -16) = 3 seconds."
      }
    ];
    let questions = [];
    let currentQuestionIndex = 0;
    let score = 0;
    let answered = false;
    let userAnswers = [];

    // Converts $...$, .math spans, and simple text like x^2, x_1, or 1/2 into MathJax.
    function formatMathContent(value) {
      if (value === null || value === undefined) return "";

      const placeholders = [];
      const protect = (html) => {
        const token = `@@MATH_PLACEHOLDER_${placeholders.length}@@`;
        placeholders.push({ token, html });
        return token;
      };

      let output = String(value);

      if (isLikelyMathExpression(output)) {
        return inlineMath(output);
      }

      output = output.replace(/\\\([\s\S]*?\\\)/g, (match) => protect(match));

      output = output.replace(
        /<span\s+class=(["'])math\1>([\s\S]*?)<\/span>/gi,
        (_match, _quote, expression) =>
          protect(`<span class="math">${inlineMath(expression)}</span>`)
      );

      output = output.replace(/\$([^$]+)\$/g, (match, expression) =>
        isLikelyMathExpression(expression)
          ? protect(inlineMath(expression))
          : match
      );

      output = output.replace(
        /(^|[^\w\\])(-?\d+)\s*\/\s*(-?\d+)(?![\w/])/g,
        (_match, prefix, numerator, denominator) =>
          `${prefix}${protect(inlineMath(`\\frac{${numerator}}{${denominator}}`))}`
      );

      output = output.replace(
        /(^|[^\w\\])([A-Za-z]\s*_\s*(?:-?\d+|[A-Za-z]|\{[^}]+\}))/g,
        (_match, prefix, expression) =>
          `${prefix}${protect(inlineMath(expression))}`
      );

      output = output.replace(
        /(^|[^\w\\])((?:[A-Za-z]|\([^<>]*?\))\s*\^\s*(?:-?\d+|[A-Za-z]|\{[^}]+\}))/g,
        (_match, prefix, expression) =>
          `${prefix}${protect(inlineMath(expression))}`
      );

      placeholders.forEach(({ token, html }) => {
        output = output.split(token).join(html);
      });

      return output;
    }

    function inlineMath(expression) {
      return `\\(${normalizeLatexExpression(expression)}\\)`;
    }

    function normalizeLatexExpression(expression) {
      return String(expression)
        .trim()
        .replace(/^\\\(|\\\)$/g, "")
        .replace(/^\$|\$$/g, "")
        .replace(/&lt;/g, "<")
        .replace(/&gt;/g, ">")
        .replace(/&le;/g, "\\leq")
        .replace(/&ge;/g, "\\geq")
        .replace(/\s*->\s*/g, " \\to ")
        .replace(/<=/g, "\\leq")
        .replace(/>=/g, "\\geq")
        .replace(/</g, "\\lt ")
        .replace(/>/g, "\\gt ")
        .replace(/(-?\d+)\s*\/\s*(-?\d+)/g, "\\frac{$1}{$2}")
        .replace(/_\s*([A-Za-z0-9]+)\b/g, "_{$1}")
        .replace(/\^\s*([A-Za-z0-9]+)\b/g, "^{$1}");
    }

    function isLikelyMathExpression(value) {
      const text = String(value).trim();
      if (!text || /<[^>]+>/.test(text)) return false;

      const withoutLatexCommands = text.replace(/\\[A-Za-z]+/g, "");
      const withoutKnownFunctions = withoutLatexCommands.replace(
        /\b(?:sin|cos|tan|log|ln|sqrt|max|min)\b/g,
        ""
      );

      if (/[A-Za-z]{2,}/.test(withoutKnownFunctions)) return false;

      const hasMathCue =
        /[=+\-*/^_<>()\[\]{},]/.test(text) ||
        /\d+\s*\/\s*\d+/.test(text) ||
        /\\[A-Za-z]+/.test(text);

      const usesSafeCharacters = /^[0-9A-Za-z\s+\-*/^_=().,\[\]{}\\<>|]+$/.test(text);

      return hasMathCue && usesSafeCharacters;
    }

    function clearRenderedMath(element) {
      if (window.MathJax?.typesetClear) {
        MathJax.typesetClear([element]);
      }
    }

    function renderMath(element) {
      if (window.MathJax?.typesetPromise) {
        MathJax.typesetPromise([element]).catch((error) => {
          console.warn("MathJax rendering failed:", error);
        });
      }
    }

    function startPractice() {
      questions = shuffleArray([...questionBank]);
      currentQuestionIndex = 0;
      score = 0;
      answered = false;
      userAnswers = [];

      document.getElementById("startScreen").classList.add("hidden");
      document.getElementById("resultScreen").classList.add("hidden");
      document.getElementById("quizScreen").classList.remove("hidden");

      renderQuestion();
    }

    function renderQuestion() {
      answered = false;

      const q = questions[currentQuestionIndex];
      const questionArea = document.getElementById("questionArea");
      clearRenderedMath(questionArea);

      document.getElementById("checkBtn").classList.remove("hidden");
      document.getElementById("nextBtn").classList.add("hidden");

      document.getElementById("questionCounter").textContent =
        `Question ${currentQuestionIndex + 1} of ${questions.length}`;

      document.getElementById("scoreCounter").textContent =
        `Score: ${score}`;

      document.getElementById("progressFill").style.width =
        `${((currentQuestionIndex) / questions.length) * 100}%`;

      if (q.multiPart) {
        questionArea.innerHTML = `
          <div class="question-title">${q.topic}</div>
          <div class="question-text">${formatMathContent(q.question)}</div>

          <div class="placeholder-note">
            ${formatMathContent(q.graphPlaceholder)}
            <br><br>
            <!-- INSERT YOUR GRAPH IMAGE OR SVG HERE IF DESIRED -->
          </div>

          ${q.parts.map((part, partIndex) => `
            <div style="margin-top: 22px;">
              <p><strong>${formatMathContent(part.label)}</strong></p>
              <div class="options">
                ${part.options.map((option, optionIndex) => `
                  <label class="option" id="option-${partIndex}-${optionIndex}">
                    <input 
                      type="radio" 
                      name="part-${partIndex}" 
                      value="${optionIndex}">
                    <span>${formatMathContent(option)}</span>
                  </label>
                `).join("")}
              </div>
            </div>
          `).join("")}

          <div id="feedback" class="feedback"></div>
        `;
      } else {
        questionArea.innerHTML = `
          <div class="question-title">${q.topic}</div>
          <div class="question-text">${formatMathContent(q.question)}</div>

          <div class="options">
            ${q.options.map((option, index) => `
              <label class="option" id="option-${index}">
                <input type="radio" name="answer" value="${index}">
                <span>${formatMathContent(option)}</span>
              </label>
            `).join("")}
          </div>

          <div id="feedback" class="feedback"></div>
        `;
      }

      renderMath(questionArea);
    }

    function checkAnswer() {
      if (answered) return;

      const q = questions[currentQuestionIndex];
      const feedback = document.getElementById("feedback");

      let isCorrect = false;
      let selectedAnswer = null;

      if (q.multiPart) {
        const selectedParts = q.parts.map((_, partIndex) => {
          const selected = document.querySelector(`input[name="part-${partIndex}"]:checked`);
          return selected ? Number(selected.value) : null;
        });

        if (selectedParts.includes(null)) {
          feedback.className = "feedback incorrect";
          feedback.innerHTML = "Please answer all parts before checking.";
          return;
        }

        isCorrect = selectedParts.every((value, index) => value === q.parts[index].answer);
        selectedAnswer = selectedParts;

        q.parts.forEach((part, partIndex) => {
          part.options.forEach((_, optionIndex) => {
            const optionElement = document.getElementById(`option-${partIndex}-${optionIndex}`);

            if (optionIndex === part.answer) {
              optionElement.classList.add("correct");
            }

            if (
              selectedParts[partIndex] === optionIndex &&
              optionIndex !== part.answer
            ) {
              optionElement.classList.add("incorrect");
            }
          });
        });

        if (isCorrect) {
          score++;
          feedback.className = "feedback correct";
          feedback.innerHTML = `Correct!<br>${formatMathContent(q.explanation)}`;
        } else {
          feedback.className = "feedback incorrect";
          feedback.innerHTML = `
            Incorrect.<br>
            ${formatMathContent(q.explanation)}
          `;
        }

      } else {
        const selected = document.querySelector('input[name="answer"]:checked');

        if (!selected) {
          feedback.className = "feedback incorrect";
          feedback.innerHTML = "Please select an answer before checking.";
          return;
        }

        selectedAnswer = Number(selected.value);
        isCorrect = selectedAnswer === q.answer;

        q.options.forEach((_, index) => {
          const optionElement = document.getElementById(`option-${index}`);

          if (index === q.answer) {
            optionElement.classList.add("correct");
          }

          if (selectedAnswer === index && index !== q.answer) {
            optionElement.classList.add("incorrect");
          }
        });

        if (isCorrect) {
          score++;
          feedback.className = "feedback correct";
          feedback.innerHTML = `Correct!<br>${formatMathContent(q.explanation)}`;
        } else {
          feedback.className = "feedback incorrect";
          feedback.innerHTML = `
            Incorrect.<br>
            Correct answer: <strong>${formatMathContent(q.options[q.answer])}</strong><br>
            ${formatMathContent(q.explanation)}
          `;
        }
      }

      renderMath(feedback);

      userAnswers.push({
        question: q.question,
        topic: q.topic,
        selected: selectedAnswer,
        correct: isCorrect,
        correctAnswer: q.multiPart
          ? q.parts.map(part => part.options[part.answer])
          : q.options[q.answer],
        explanation: q.explanation
      });

      answered = true;
      document.getElementById("checkBtn").classList.add("hidden");
      document.getElementById("nextBtn").classList.remove("hidden");
      document.getElementById("scoreCounter").textContent = `Score: ${score}`;
    }

    function nextQuestion() {
      currentQuestionIndex++;

      if (currentQuestionIndex >= questions.length) {
        showResults();
      } else {
        renderQuestion();
      }
    }

    function showResults() {
      document.getElementById("quizScreen").classList.add("hidden");
      document.getElementById("resultScreen").classList.remove("hidden");

      document.getElementById("progressFill").style.width = "100%";

      const percent = Math.round((score / questions.length) * 100);

      document.getElementById("finalScore").textContent =
        `${score}/${questions.length} (${percent}%)`;

      document.getElementById("finalMessage").textContent =
        percent >= 85
          ? "Excellent work. You are showing strong course mastery."
          : percent >= 70
          ? "Good work. Review the incorrect answers and practice again."
          : "Keep practicing. Focus on the explanations and try again.";

      const reviewArea = document.getElementById("reviewArea");
      clearRenderedMath(reviewArea);

      reviewArea.innerHTML = userAnswers.map((item, index) => `
        <div class="review-item">
          <strong>${index + 1}. ${item.topic}</strong>
          <p>${formatMathContent(item.question)}</p>
          <p>
            Result:
            <strong style="color:${item.correct ? 'var(--correct)' : 'var(--incorrect)'}">
              ${item.correct ? "Correct" : "Incorrect"}
            </strong>
          </p>
          ${!item.correct ? `
            <p>Correct answer: <strong>${
              Array.isArray(item.correctAnswer)
                ? item.correctAnswer.map(formatMathContent).join(" / ")
                : formatMathContent(item.correctAnswer)
            }</strong></p>
          ` : ""}
          <p>${formatMathContent(item.explanation)}</p>
        </div>
      `).join("");

      renderMath(reviewArea);
    }

    function restartPractice() {
      startPractice();
    }

    function shuffleArray(array) {
      for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
      }
      return array;
    }
  </script>
  <script>
    MathJax = {
      tex: {
        inlineMath: [['\\(', '\\)']],
        processEscapes: true
      },
      chtml: {
        scale: 1.02
      }
    };
  </script>
  <script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</body>
</html>
