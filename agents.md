# Directiva de Sistema: Implementación Landing Page RBBR (ASCII Art & Retro-Mono UI)

Actúas como un **Desarrollador Frontend Senior e Ingeniero UI/UX**. Tu objetivo es construir la landing page completa, funcional y responsive en un único archivo `index.html` autocontenido, respetando la identidad tipográfica, el layout y las artes ASCII estructuradas.

---

## 1. Tipografía y Fuentes de Google

Configura e inyecta en el `<head>` las fuentes requeridas desde Google Fonts:

1. **Logo RBBR:**
   * Fuente: `Jaini Purva`
   * Importación: `https://fonts.googleapis.com/css2?family=Jaini+Purva&display=swap`
   * Clase Tailwind o CSS: `font-['Jaini_Purva']`
2. **Cuerpo general, títulos y Arte ASCII:**
   * Fuente: `Roboto Mono`
   * Importación: `https://fonts.googleapis.com/css2?family=Roboto+Mono:ital,wght@0,300;0,400;0,600;0,700;1,400&display=swap`
   * Configuración base: `font-mono` / `font-['Roboto_Mono']` aplicada a todo el documento.

---

## 2. Reglas de Renderizado para Arte ASCII

El arte ASCII no debe desfigurarse bajo ninguna resolución. Sigue estas directivas estrictas:

* **Etiquetas requeridas:** Utiliza bloques `<pre><code>` para renderizar el arte.
* **Preservación de espaciado:**
  * Aplica `white-space: pre` y `user-select: none`.
  * La tipografía en el ASCII debe ser estrictamente `font-['Roboto_Mono']` con line-height ajustado (`leading-none` o `leading-[1.05]`) y tamaño escalable (`text-[7px] sm:text-[9px] md:text-[11px]`).
* **Composición y Superposición (Espejo + Foto):**
  * El diseño cuenta con un marco (**el espejo**) y un sujeto en primer plano (**la foto**).
  * El contenedor visual debe estructurarse usando posicionamiento relativo/absoluto o CSS Grid superpuesto:
    * **Fondo:** Capa del espejo ASCII.
    * **Frente / Centro:** Capa de la foto ASCII situada frente/dentro del hueco del espejo.
    * Asegura contraste visual adecuado (ej. opacidad sutil o color de acento diferenciado para la silueta delantera frente al marco).
* **Scroll y desborde:** Envuelve los bloques ASCII en un contenedor con `overflow-x-auto` o `overflow-hidden` centrado (`flex items-center justify-center`) para evitar que desborde la pantalla en móviles.

---

## 3. Arquitectura de Layout y Viewport

1. **Hero Section:**
   * Utiliza `min-h-[100dvh]` para asegurar estabilidad en navegadores móviles.
   * Disposición vertical centrada y balanceada.
2. **Contenedor Maestro:**
   * Envuelve el contenido en un contenedor maestro: `w-full max-w-5xl mx-auto px-4 sm:px-6`.
3. **Navegación / Header:**
   * Logo `RBBR` destacado con `font-['Jaini_Purva']`.
   * Enlaces de anclaje limpios en `font-['Roboto_Mono']`.

---

## 4. Botones, Cards y Redirección

* Todos los elementos interactivos que redirijan a enlaces externos deben implementarse con etiquetas `<a>` usando `target="_blank"` y `rel="noopener noreferrer"`.
* Microinteracciones con estética terminal/retro:
  * Cambios de borde o fondo (`hover:bg-neutral-800`, `hover:border-neutral-400`).
  * Transición suave: `transition-all duration-250`.
* Enlaces con placeholders explícitos para reemplazo inmediato (ej. `href="https://github.com/..."`, `href="https://linkedin.com/..."`).

---

## 5. Assets ASCII Definidos

### Asset A: El Espejo (Marco / Fondo)
```text
                                     -#=.:                                      
                                  .:#:=-*+*.=.                                  
                                  .:==+-:*+*=-                                  
                             +.==:++%.-=*=-%%%=.:=.                             
                         =+.* %+:=:+#=%*-*=#*:%=#= =-+:                         
                      ..#%-.-:-+#=#*-%+#-**=##=*===:=*%%:.                      
                    :-#==#%%%+-:*+=-##+%+*%*-+*#:*-##%%#*+#:                    
                    +#-+-%%%#=+*******#+:++****###+#%%%+#=#-                    
                  ::+-+=#*#*==-.::+=:=**++:=+-.:=+**#+%#+*+=*=                  
              ---+=+==.:===:.+:#+=*#+:-=-:-##+=-==.:++*%:#**:=*-*=              
           :-=+. :++..*-- =:.+*:=              **#=*-.:+*#:=+%==. .==           
          .-.*=*#:=:*=- +*=*-                     *=+-:..=+#-#*#*:+.:           
         =::-::=#**=:.+=-++                          =#+:.:=*%#%#::+:--         
        :=-*.:**==--:=.-=                              :+:: =+%:*%===.#.        
        .+ .-=*-+::=+:+=                                 #=:.-=#.*#-.:::        
         =.:-%==..+*-.                                    **+..=#.#=+:.         
         ##*+++:.+#:.                                      =+*..=%=:*--         
          #-*=-:-=-.                                        =+-.:+#=%*.         
       :=:+--::.-==                                          #=. =***:#.:       
       *+-***..*=::                                           *:- =#-*+.-       
       %%%*-...:=.                                            +--.-+#**#=       
      #-+*#= :**..                                            :*-:.=#:#%.=      
      %===+= .+=-                                              #+. -*+-=+#=     
      ++=*=..::..                                              -=- =++=+.=-     
      :-*:=-.:::.                                              -=*.-*%+=:.      
     =%%**=:=-=.:                                              ++*.*++#*=*+.    
     -*+==.-*==..                                              *=+.#==#::.-     
      -#+#-+.::..                                              ++#.:###+.=      
      **-#....:+.                                              -*=.:=##+ -:     
      *-==-: .=:-                                              *+: :=+:-.#=     
      **%%#= .#+:                                              #.- :*:**++      
       *+**+..:+..                                            *-+..:*.:%-       
       *#::+...+--                                            #*. -=+#=:*:      
       =**%:+ :-=-.                                          *+=..:%:*+:..      
         --:+-..*-.                                          #-: :=-%*=         
         *-.*:...-*-                                        *+=.:-#*-*.         
          ==:%+.:::=-                                      -=#.::*:-:+=         
           .-#*+..::+-                                    ==#..-#.#+#:-         
        +%:.*:***...--::                                 **+.-=#:*=*-:-=        
         +*.::=##=:. +*:.                              **+-.=+*:#-=+:+--        
          .#:=: .#:-  ::-:-                           *=+::=+#+*=*#+:-          
           :#+*:+...+.. +.---                      -#+*=:=-**##:#:#=-.          
              *#.+##-.-. .==+=*+                :*==:-:--*--=*+==+.             
               *-=*-#.:*+:..:+=#:-*-+=    =-+#+-*-=:.:-*--+**+*=+-              
                    *+*.#%:+---.:=*+--###%+-+*-::==-*+**%-*- .                  
                    +=-%:=-*#-*+++++===%*==+++++*#-#%**#%:=.                    
                     :#*+%#%%=:###+**:=*:*#*=**#=**+%%%#-=*=                    
                        ##+--*-#*=%##*#+:+%-+%-+%+.-+:%%=                       
                           .  +##:*##**%%-:-*+#*#.. ..                          
                              ..=*#+*...*==*%+-:::                              
                                  =-#.:-*-:.#*                                  
                                       =..                                      
```

### Asset B: La Foto (Sujeto / Delante del Espejo)
```text
                                    .. -.                                       
                                 -+*#*****#:                                    
                              :++**+*--=+#**:                                   
                             .**#*#++==++=####.                                 
                              ###++**--*#++*#*                                  
                            .*##+=--====-:.:+.=                                 
                            * .#=-=---=-+=--##                                  
                              *#*-===*+===--##                                  
                              *##%===++==+%##*.                                 
                             *.*##*+***+==###**                                 
           --:.           *%#%#++++==*%%#=                                  
           ==-:        .=*++**-+---=###**#*#+.                               
           ===-    =+******+***+###**#******#+*++....  . .....               
           -==-  .+*+*#++++++++*+*++*++++=.++#+***+.............              
.          =+--:=*+*#*+*+++++:   +  ++ ---=.+-****++............             
 .       ....=::  ++*#***---+-- := -=::=+:=: .=+++*%#**+..........              
.      ::::......:+***###.-=*=--+ +:+=*:--- +++===**#***+...........             
.      ::::....:+***###.-=*=--+ +:+=*:--- +++===**#*******+.......................
```

---

## 6. Salida Esperada

* Devuelve **únicamente** el código HTML completo (`<!DOCTYPE html>` a `</html>`) dentro de un único bloque de código Markdown ````html ... ````.
* No omitas código ni utilices comentarios de elisión tipo `<!-- resto de la página aquí -->`.