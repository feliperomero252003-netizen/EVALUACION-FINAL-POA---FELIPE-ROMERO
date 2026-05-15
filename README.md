# EVALUACION-FINAL-POA---FELIPE-ROMERO
A continuación esta el desarrollo de la Evaluación POA 
team_hours = [
    ["Alice", 8, 9, 7, 8, 8],    # Total: 40
    ["Bob", 10, 8, 9, 10, 9],   # Total: 46
    ["Charlie", 7, 7, 7, 7, 7], # Total: 35
    ["Diana", 8, 8, 8, 8, 8]    # Total: 40
]

STANDARD_HOURS_THRESHOLD = 40

print("Matriz de horas trabajadas:")
for row in team_hours:
    print(row)



def calculate_and_classify_hours(team_data, threshold):
    
    results = []
    for resource_data in team_data:
        name = resource_data[0]
        daily_hours = resource_data[1:] # Horas de Lunes a Viernes
        total_hours = sum(daily_hours)

        if total_hours > threshold:
            classification = "Sobretiempo"
        else:
            classification = "Horario Estándar"

        results.append((name, total_hours, classification))
    return results


team_summary = calculate_and_classify_hours(team_hours, STANDARD_HOURS_THRESHOLD)

print("\n--- Resumen de Horas Semanales ---")
for name, total_hours, classification in team_summary:
    print(f"Recurso: {name}, Total Horas: {total_hours}, Clasificación: {classification}")


print("\n--- Búsqueda de Horas por Recurso ---")
resource_to_find = input("Introduce el nombre del recurso a buscar: ")

found = False
for name, total_hours, classification in team_summary:
    if name.lower() == resource_to_find.lower():
        print(f"Recurso: {name}, Total Horas: {total_hours}, Clasificación: {classification}")
        found = True
        break

if not found:
    print(f"El recurso '{resource_to_find}' no fue encontrado en la lista.")
