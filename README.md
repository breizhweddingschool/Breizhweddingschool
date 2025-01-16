<!DOCTYPE html>
<html>
<head>
    <title>Quiz Interactif</title>
    <script>
        function calculateScore() {
            let score = 0;
            const correctAnswers = ["a", "b", "c"]; // Remplacez par les bonnes réponses
            const userAnswers = [
                document.querySelector('input[name="q1"]:checked')?.value,
                document.querySelector('input[name="q2"]:checked')?.value,
                document.querySelector('input[name="q3"]:checked')?.value
            ];
            userAnswers.forEach((answer, index) => {
                if (answer === correctAnswers[index]) score++;
            });

            const percentage = (score / correctAnswers.length) * 100;
            document.getElementById("result").innerText = `Votre score : ${percentage.toFixed(2)}%`;

            sendEmail(percentage);
        }

        function sendEmail(score) {
            const email = document.getElementById("email").value;
            if (!email) {
                alert("Veuillez saisir votre adresse e-mail !");
                return;
            }
            alert(`Les résultats seront envoyés à : ${email} avec un score de ${score}%`);
            // Vous pouvez intégrer un outil comme EmailJS pour envoyer l'email réellement
        }
    </script>
</head>
<body>
    <h1>Quiz Interactif</h1>
    <form>
        <label for="email">Votre e-mail : </label>
        <input type="email" id="email" required><br><br>

        <h3>Question 1 : Quel est le résultat de 2 + 2 ?</h3>
        <label><input type="radio" name="q1" value="a"> 4</label><br>
        <label><input type="radio" name="q1" value="b"> 5</label><br>

        <h3>Question 2 : Quelle est la couleur du ciel ?</h3>
        <label><input type="radio" name="q2" value="a"> Rouge</label><br>
        <label><input type="radio" name="q2" value="b"> Bleu</label><br>

        <h3>Question 3 : Combien font 3 x 3 ?</h3>
        <label><input type="radio" name="q3" value="a"> 6</label><br>
        <label><input type="radio" name="q3" value="c"> 9</label><br><br>

        <button type="button" onclick="calculateScore()">Soumettre</button>
    </form>
    <p id="result"></p>
</body>
</html>
