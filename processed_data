import os
import cv2

input_folder = "dataset"
output_folder = "processed"

# Create processed folder if it doesn't exist
if not os.path.exists(output_folder):
    os.makedirs(output_folder)

for person in os.listdir(input_folder):
    person_path = os.path.join(input_folder, person)
    
    if os.path.isdir(person_path):
        output_person_path = os.path.join(output_folder, person)
        os.makedirs(output_person_path, exist_ok=True)
        
        for img_name in os.listdir(person_path):
            img_path = os.path.join(person_path, img_name)
            
            img = cv2.imread(img_path)
            if img is None:
                continue
            
            # Resize image
            img = cv2.resize(img, (224, 224))
            
            # Normalize image
            img = img / 255.0
            
            # Save processed image
            output_path = os.path.join(output_person_path, img_name)
            cv2.imwrite(output_path, (img * 255).astype("uint8"))
