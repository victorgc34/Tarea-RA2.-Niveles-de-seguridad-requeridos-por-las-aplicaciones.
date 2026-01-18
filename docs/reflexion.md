# Apartado 4 – Reflexión sobre los riesgos de las aplicaciones

Al analizar la aplicación del lavadero, podemos observar que los riesgos asociados son **muy limitados**, tanto por su funcionalidad como por su entorno de ejecución. Los posibles problemas se centran en la interrupción del servicio (caída temporal del lavadero) o errores en los cobros, pero **no existen riesgos de impacto crítico ni compromisos de datos sensibles externos**, ya que la aplicación normalmente se ejecuta en un entorno aislado y sin conexión a internet.

Comparando con otros tipos de aplicaciones, como las bancarias, de salud o redes sociales, los riesgos cambian drásticamente:

- Una aplicación bancaria implica riesgos de fraude, robo de fondos y fuga de datos financieros, por lo que requiere controles muy estrictos de autenticación, autorización, cifrado y monitoreo.
- Una aplicación de salud maneja datos médicos confidenciales, por lo que las brechas pueden afectar directamente la privacidad de los pacientes y generar responsabilidad legal.
- Una red social debe proteger grandes volúmenes de datos personales, prevenir suplantación de identidad, y gestionar el contenido malicioso, requiriendo controles avanzados de validación, filtrado y privacidad.

La reflexión principal es que **los riesgos de una aplicación dependen directamente de su propósito, los datos que maneja y el impacto potencial de una vulnerabilidad**. Por ello, no todas las aplicaciones requieren el mismo nivel de seguridad.