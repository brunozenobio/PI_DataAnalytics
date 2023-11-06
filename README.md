# PI_DataAnalytics



Aumento de la fibra optica en general.

PRovincias con una alta tase de acceso y baja velocidad, baja densiadad pob lacion -> fibra optica no es la solucion, KPI aumento de wireless ->wireles como solucion particular en estas zonas 
- La fibra óptica se utiliza para transportar señales de manera segura y eficiente a través del espacio, gra 
ciencias que permiten una transmisión constante de información a distancias cortas o largas.
- El aumento de la demanda por parte de los usuarios ha llevado al crecimiento de la fibra óptica en 
general.
### Factores clave que influyen en el crecimiento de la fibra óptica:
1. Demanda creciente: La demanda de servicios de telecomunicaciones es cada vez mayor, lo que ha generado un aumento en las necesidades de fibra óptica.
2. Avances tecnológicos: Los avances en la ciencia y la tecnología han mejorado la calidad y la eficiencia de la fibra óptica, lo que ha llevado a un mayor uso de este medio.
3. Inversión económica: La inversión en infraestructuras de fibra óptica puede ser rentable, especialmente si se considera su durabilidad y capacidad para soportar grandes cantidades de tráfico.

4. Mejora en la calidad de vida: Con el auge de Internet y redes móviles, la conectivad se ha vuelto fundamental para la sociedad actual. La fibra óptica ofrece una velocidad y calidad de conexión superior a otras opciones, lo que mejora la experiencia del usuario.
5. Seguridad: La fibra óptica es un medio seguro para transferir datos ya que no hay interferencia visible ni audible, lo que reduce el riesgo de ataque cibernético.

6. Flexibilidad: La fibra óptica permite adaptarse a diferentes requerimientos de tráfico,lo que facilita la expansión de la red sin afectar la capacidad total.
7. Rentabilidad: A medida que la demanda crece, la fibra óptica ofrece una renta potencia, lo que atrae a nuevos inversores.
8. Desarrollo sostenible: La fibra óptica es un recurso renovable, lo que significa que no hay
ninguna cantidad limitada de ella disponible. Esto permite un desarrollo sostenible sin preocupaciones.


Diff_CableModem_FibraOptica = ('acces_internet acceso_tec_provincia'[Fibra_optica]/ ('acces_internet acceso_tec_provincia'[Fibra_optica] + 'acces_internet acceso_tec_provincia'[Cablemodem]) * 100)

Total cambio Fibra Cablemodem a Fibra Optica = CALCULATE(SUM('acces_internet acceso_tec_provincia'[Diff_CableModem_FibraOptica]))

Total Diferencia año anterior = CALCULATE([Total cambio Fibra Cablemodem a Fibra Optica],PREVIOUSYEAR('acces_internet acceso_tec_provincia'[FechaTrimestre]))

Tasa anual Fibra optica Cable Modem = [Total cambio Fibra Cablemodem a Fibra Optica] - [Total Diferencia año anterior]


FechaTrimestre = DATE('acces_internet acceso_tec_provincia'[Año], ('acces_internet acceso_tec_provincia'[Trimestre] - 1) * 3 + 1, 1)



#### AUMENTO FIBRA OPTICA EN TUCUMAN
Según una nota de Infobae, el Enacom incrementó la inversión en el Proyecto Refefo para la expansión de la red de fibra óptica en Jujuy, Salta y Tucumán a $ 2.5 mil millones, a través de la Resolución 1550/2023 publicada en octubre de 20202.