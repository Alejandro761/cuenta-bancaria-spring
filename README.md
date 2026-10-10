# Cajero automático — Spring Core e inyección de dependencias

**Autor:** Alejandro Elías Castañeda Ibarra

## Cómo correrlo

    ./correr.sh App final-app
    ./probar.sh final

## Las piezas

| Bean | Clase | Cómo lo declara Spring (`@Component` o `@Bean`) | Singleton o prototype |
|---|---|---|---|
| cajeroAutomatico | CajeroAutomatico | Component | Singleton |
| sesionCajero | SesionCajero | Component | prototype |
| antifraudeEstricto | AntifraudeEstricto | Component | Singleton |
| antifraudePorMonto | AntifraudePorMonto | Component | Singleton |
| reloj | Clock | Bean | Singleton |
| notificadorConsola | NotificadorConsola | Component | Singleton |
| repositorioEnMemoria | RepositorioEnMemoria | Component | Singleton |
| sesionCajero | SesionCajero | Component | prototype |

## Boleto de salida

1. ¿Qué es la inyección de dependencias? Explícalo con el cajero, en tus palabras.

    Es una forma de trabajar, en vez de construir el cajero y sus componentes juntos, se construyen los componentes a parte y se van integrando al cajero. Si hace falta reparar o actualizar una pieza, solo cambiamos esa pieza y no todo el cajero.

2. En la MP-1, ¿quién decidía qué antifraude usaba el cajero? ¿Y desde la MP-2?

    El método main la crear una instancia de ServicioAntifraude con AntifraudePorMonto.

3. ¿Cuándo usarías `@Bean` en vez de `@Component`? Da el ejemplo de hoy.

    Bean lo usaría cuando necesite instancias de clases de Java, como Clock. Component para servicios propios que cumplen una tarea determinada en la aplicación, como el servicio de antifraude o el notificador.

4. ¿Qué gana: `@Primary` o `@Qualifier`? ¿Por qué tiene sentido?

    Gana @Qualifier ya que, en el constructor del cajero, al inyectar el ServicioAntifraude de específica cual implementación tomar. Primary se toma cuando no se específica cual implementación tomar.

5. En tu proyecto de Empleados de la Semana 3 nunca escribiste `@ComponentScan`. ¿Quién lo hace? (Pista: abre la
   anotación `@SpringBootApplication` con `Ctrl+clic` y busca las anotaciones que tiene arriba.)

    La anotación @SpringBootApplication ya contiene la anotación @ComponentScan, la configuta automáticamente.
    