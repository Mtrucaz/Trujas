<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Comentarios y Valoraciones</title>
    <style>
        body {
            background-color: #add8e6; /* Fondo azul claro */
            font-family: Arial, sans-serif;
            padding: 20px;
            text-align: center;
        }
        .comment-box {
            background: white;
            border-radius: 5px;
            padding: 20px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
        }
        .stars {
            display: flex;
            justify-content: center;
            margin-bottom: 10px;
        }
        .star {
            font-size: 30px;
            cursor: pointer;
            color: gray;
        }
        .star.selected {
            color: gold; /* Color dorado para estrellas seleccionadas */
        }
    </style>
</head>
<body>
    <h1>TRUJAS TO FURIOUS</h1> <!-- Título agregado -->
    
    <div class="comment-box">
        <div class="stars" id="star-rating">
            <span class="star" data-value="1">★</span>
            <span class="star" data-value="2">★</span>
            <span class="star" data-value="3">★</span>
            <span class="star" data-value="4">★</span>
            <span class="star" data-value="5">★</span>
        </div>
        <textarea id="comment" rows="4" placeholder="Escribe tu comentario aquí..."></textarea><br>
        <button onclick="submitComment()">Enviar</button>
    </div>

    <h2>Comentarios</h2>
    <div id="comments-section"></div>

    <script>
        const stars = document.querySelectorAll('.star');
        let rating = 0;

        stars.forEach(star => {
            star.addEventListener('click', () => {
                rating = star.dataset.value;
                stars.forEach(s => s.classList.remove('selected'));
                star.classList.add('selected');
            });
        });

        function submitComment() {
            const comment = document.getElementById('comment').value;
            const commentsSection = document.getElementById('comments-section');

            if (rating > 0 && comment) {
                const newComment = document.createElement('div');
                newComment.innerHTML = `<strong>Valoración: ${rating} Estrellas</strong><p>${comment}</p>`;
                commentsSection.appendChild(newComment);
                
                // Resetear valores
                document.getElementById('comment').value = '';
                rating = 0;
                stars.forEach(s => s.classList.remove('selected'));
            } else {
                alert('Por favor, selecciona una valoración y escribe un comentario.');
            }
        }
    </script>
</body>
</html>
