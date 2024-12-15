from moviepy.editor import *
from PIL import Image

# Cargar la imagen subida
image_path = "/mnt/data/WhatsApp Image 2024-12-14 at 8.55.18 PM.jpeg"
background = Image.open(image_path)

# Crear un clip de imagen estática
image_clip = ImageClip(image_path).set_duration(10)  # Duración de 10 segundos

# Agregar música navideña
music = AudioFileClip("navidad.mp3").set_duration(10)  # Reemplaza con un archivo MP3 de tu elección

# Agregar texto animado
text_clip = TextClip(
    "¡Te esperamos en nuestra Chocolatada Anual!", fontsize=50, color='white', font='Amiri-Bold'
).set_position('center').set_duration(10)

# Combinar la imagen con el texto animado
final_clip = CompositeVideoClip([image_clip, text_clip])

# Añadir música al video
final_clip = final_clip.set_audio(music)

# Exportar el video
final_video_path = "/mnt/data/chocolatada_anual_navidad.mp4"
final_clip.write_videofile(final_video_path, fps=24)


