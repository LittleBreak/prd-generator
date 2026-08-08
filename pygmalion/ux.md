1. 初始化 Prompt（High-Level）                                                                           
                                                                                                           
  A mobile-first creative app called "Pygmalion" that lets users draw simple sketches and convert them into
   beautiful AI-generated artwork. The app has 3 screens: a style selection homepage, a full-screen canvas 
  drawing board, and a result preview page. The vibe is playful, creative, and approachable — designed for 
  non-artists aged 18-35. Clean, modern UI with generous whitespace, soft rounded corners, and a light     
  background.                                                                                              
                                                                                                           
  ---                                                                                                      
  2. 逐页面细化 Prompt                                                                                     
                                                                                                           
  P.1 首页（风格选择页）                                                                                   
                                                                                                           
  Homepage / Style Selection screen. Display 4 large art style cards in a 2×2 grid layout, each card       
  showing a preview image and style name label. The 4 styles are: "动漫/卡通" (Anime/Cartoon — show a      
  colorful anime-style illustration), "水彩/油画" (Watercolor/Oil Painting — show a soft watercolor        
  landscape), "像素风" (Pixel Art — show a retro 16-bit game scene), "写实/摄影" (Realistic/Photography —  
  show a photorealistic nature photo). Each card has rounded corners (12px), a subtle shadow, and a tap    
  highlight effect. Top of the page shows the app logo "Pygmalion" with a tagline "画一画，变精美" (Sketch 
  it, make it beautiful). No navigation bar — full-screen immersive layout. Mobile viewport 375px width.   
                                                                                                           
  P.2 画板页（Canvas Page）                                                                                
                                                                                                           
  Canvas / Drawing Board screen. Full-screen white canvas area taking up ~70% of the screen. Top bar: left 
  side shows a back arrow and the currently selected style name as a tag/chip (e.g. "动漫/卡通"), right    
  side shows a prominent "生成" (Generate) primary button in brand accent color. Bottom fixed toolbar with 
  icon buttons in a single row: Pen tool (active by default), Eraser tool, Shape tool (dropdown for        
  rectangle/circle/triangle), Undo arrow, Redo arrow, and a Trash/Clear icon. Below the toolbar icons, show
   a horizontal scrollable color palette strip with 12 color circles: black, white, red, orange, yellow,   
  green, blue, purple, pink, brown, gray, cyan. The selected color has a ring highlight. When Pen is       
  selected, show a small 3-step size slider (thin/medium/thick) above the color palette. Below the canvas  
  area and above the toolbar, include a single-line text input field with placeholder                      
  "描述你想要的画面细节..." (Describe the details you want...) and a 500-character limit indicator.        
  Mobile-optimized touch-friendly layout, all tap targets at least 44px.                                   
                                                                                                           
  P.3 结果预览页（Result Preview Page）                                                                    
                                                                                                           
  Result Preview screen. Full-screen display of the AI-generated image, centered, with pinch-to-zoom       
  support. Dark semi-transparent overlay behind the image for focus. Bottom action bar with 3 buttons in a 
  row: "保存到相册" (Save to Album) as primary filled button with a download icon, "重新生成" (Regenerate) 
  as secondary outlined button with a refresh icon, "返回画板" (Back to Canvas) as text/ghost button with a
   back arrow icon. When saving succeeds, show a brief toast notification "已保存到相册" (Saved to Album). 
  Top-right corner has a small "×" close button to return to homepage.                                     
                                                                                                           
  ---                                                                                                      
  3. 主题控制 Prompt                                                                                       
                                                                                                           
  Colors: Use a clean light theme. Background is off-white (#FAFAFA). Primary accent color is a warm       
  coral/orange (#FF6B4A) for the Generate button and selected states. Secondary color is soft indigo       
  (#6C5CE7) for style card accents. Text uses near-black (#1A1A2E) for headings and dark gray (#4A4A68) for
   body text.                                                                                              
                                                                                                           
  Fonts: Use a rounded, friendly sans-serif font (like Nunito or similar). Headings are bold, body text is 
  regular weight. The app logo "Pygmalion" uses a slightly playful display font.                           
                                                                                                           
  Borders & Shapes: All buttons have fully rounded corners (pill-shaped for primary buttons, 8px radius for
   secondary). Cards have 12px rounded corners with soft box shadows. Input fields have a 1px solid light  
  gray border with 8px radius.                                                                             
                                                                                                           
  ---                                                                                                      
  4. Loading 状态 Prompt                                                                                   
                                                                                                           
  On the Canvas page, when the user taps "生成" (Generate), show a full-screen loading overlay with a      
  centered animation — a pencil sketch morphing into a colorful painting (or a simple spinning brush icon).
   Below the animation, display text "AI 正在创作中..." (AI is creating...) in the secondary text color.   
  The overlay has a semi-transparent white background (#FFFFFF CC). Include a small "取消" (Cancel) text   
  button below the loading text.                                                                           
                                                                                                           
  ---                                                                                                      
  5. 错误状态 Prompt                                                                                       
                                                                                                           
  When generation fails, show an inline error card on the canvas page with an illustration of a sad        
  paintbrush, error message "生成失败，请重试" (Generation failed, please retry), and a "重试" (Retry)     
  button in the primary accent color. When the canvas is empty and the user tries to tap Generate, the     
  button should appear disabled (grayed out) with a tooltip "请先在画板上绘制草图" (Please draw a sketch   
  first).                                                                                                  
                                                                                                           