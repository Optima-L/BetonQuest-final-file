# BetonQuest-
npcs:
 '207': 'mark' 

effectlib:
  default:
    class: LoveEffect
    iterations: 20
    particle: villager_happy
    offset: 0,-1.5,0
    interval: 100
    check_interval: 100
    disabled: false
    npcs:
      - 207

conversations:
  mark: #ВОТ ТУТ ИМЯ РАЗГОВОРА
    interceptor: packet,simple
    quester: "Марк" #ИМЯ НПС
    first: "npc1,npc5" #FIRST ЭТО ПЕРВЫЙ ДИАЛОГ КОТОРЫЙ БУДЕТ НПС ГОВОРИТЬ
    stop: false
    NPC_options:
       npc1:
        text: "Помогите пожалуйта, мою ферму атаковали вредители."
        pointer: "player1" #ВОТ ТУТ ОПРЕДЕЛЯЕМ КУДА БУДЕТ ОТПРАВЛЯЕТЬ ЭТОТ ДИАЛОГ
        condition: '!has_tag_complete' #только уже тут перед условием ставим знак ! это будет означать что у игрока не должно быть этого тега!
       npc2:
        text: "Прошу убей их, они портят мою пшеницу, моя семья очень нуждаетя в еде."
        pointer: "player2,player3" #ТУТ ТАКЖЕ 
       npc3:
        text: "Спасибо что согласился!"
       npc4:
        text: "Жаль, что ты отказался."
       npc5:
        text: "Спасибо что помог!" 
        condition: 'has_tag_complete'  #ЭТО УСЛОВИЕ ЧТО ИГРОК ВЫПОЛНИЛ КВЕСТ И ПОЛУЧИЛ ТЕГ 
    player_options:
       player1:
        text: "Чем помочь?"
        pointer: "npc2" #ТУТ ТАКЖЕ 
       player2:
        text: "Хорошо, я помогу тебе."
        pointer: "npc3" #ТУТ ТАКЖЕ
        event: 'tag_and_obj' 
       player3:
        text: "Прости, но я занят"
        pointer: "npc4" #ТУТ ТАКЖЕ



events:
  reward: "money +45" #ЭТО НАГРДА 10 шекелей
  reward1: mmoclassexperience 780
  soundd: 'notify sound:ITEM_FIRECHARGE_USE'
  notify: "notify  \n &6Квест выполнен! \n &aВы заработали 400 опыта и 45 шекелей. \n "
  tag: tag add questStart
  give_obj: 'objective add NEGR_GAY'
  tag_and_obj: folder tag,give_obj
  tag_complete: tag add tag_complete
  
conditions: 
  WARRIOR: mmoclass WARRIOR
  has_tag: tag questStart 
  has_tag_complete: tag tag_complete

objectives:
  NEGR_GAY: mmobkill GOBLIN_PEST amount:6 events:reward,reward1,tag_complete,notify,soundd conditions:has_tag

#ash	
#barrier	
#block_crack	
#block_dust	
#bubble_column_up	
#bubble_pop	
#campfire_cosy_smoke	
#campfire_signal_smoke	
#cloud	
#composter	
#crimson_spore	
#crit	
#crit_magic	
#current_down	
#damage_indicator	
#dolphin	
#dragon_breath	
#drip_lava	
#drip_water	
#dripping_dripstone_lava	
#dripping_dripstone_water	
#dripping_honey	
#dripping_obsidian_tear	
#dust_color_transition	
#electric_spark	
#enchantment_table	
#end_rod	
#explosion_huge	
#explosion_large	
#explosion_normal	
#falling_dripstone_lava	
#falling_dripstone_water	
#falling_dust	
#falling_honey	
#falling_lava	
#falling_nectar	
#falling_obsidian_tear	
#falling_spore_blossom	
#falling_water	
#fireworks_spark	
#flame	
#flash	
#glow	
#glow_squid_ink	
#heart	
#item_crack	
#landing_honey	
#landing_lava	
#landing_obsidian_tear	
#lava	
#legacy_block_crack	
#legacy_block_dust	
#legacy_falling_dust	
#light	
#mob_appearance	
#nautilus	
#note	
#portal	
#redstone	
#reverse_portal	
#scrape	
#slime	
#small_flame	
#smoke_large	
#smoke_normal	
#sneeze	
#snow_shovel	
#snowball	
#snowflake	
#soul	
#soul_fire_flame	
#spell	
#spell_instant	
#spell_mob	
#spell_mob_ambient	
#spell_witch	
#spit	
#spore_blossom_air	
#squid_ink	
#suspended	
#suspended_depth	
#sweep_attack	
#totem	
#town_aura




menu_conv_io: #ЭТО ПРОСТ НАСТРОЙКИ РАЗГОВОРА ЕГО ПРОСТО СТАВИИШЬ В КОНЕЦ ЧТОБ НЕ МЕШАЛ
  line_length: 70
  refresh_delay: 180 
  selectionCooldown: 10

  npc_wrap: '&l &r' 
  npc_text: '&l &r&f{npc_text}' 
  npc_text_reset: '&f' 
  option_wrap: '&r&l &l &l &l &r' 
  option_text: '&l &l &l &l &r&8[ &b{option_text}&8 ]' 
  option_text_reset: '&b' 
  option_selected: '&l &r &r&a✔&r &8» &f&n{option_text}&8 «' 
  option_selected_reset: '&f' 
  option_selected_wrap: '&r&l &l &l &l &r&f&n'

  control_cancel: 'sneak'
  control_select: 'jump' 
  control_move: 'scroll,move' 

  npc_name_type: chat 
  npc_name_align: center 
  npc_name_format: '&e» &6{npc_name} &e«' 
  npc_name_newline_separator: true 
