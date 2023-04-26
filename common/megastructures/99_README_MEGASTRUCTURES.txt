#my_piquant_megastructure = {
#	entity = "bawling_pink_rainbow_graphics"
#	construction_entity = "bawling_pink_rainbow_graphics_construction"
#	portrait = "GFX_my_piquant_megastructure_background"
#	upgrade_desc = default|hide		# default: 'デフォルト'。非表示にするには 'hide' を使って、このステージをアップグレードの一覧から隠します。
#	upgrade_from = {
#		my_flamboyant_megastructure
#	}
#	prerequisites = { "tech" }		# 必要技術
#	potential = {}					# trigger, scope: country
#	possible = {}					# trigger, scope: galactic object, from: country
#	build_time = 5					# days
#	victory_score = 1000			# そのメガストラクチャーを所有するプレイヤーの勝利スコア
#	build_cost = {
#		minerals = 8
#		energy = 13
#		influence = 21
#	}
#	monthly_production = {
#		energy = 34
#	}
#	maintenance = {
#		energy = 10
#	}
#	country_modifier = {}
#
#	placement_rules = {
#		planet_possible = {}		# trigger, scope: planet
#	}
#
#	on_build_start = {}				# effects, scope: galactic object, from: country, fromfrom: megastructure instance (when upgrading existing megastructure)
#	on_build_cancel = {}			# effects, scope: galactic object, from: country
#	on_build_complete = {}			# effects, scope: galactic object, from: country, fromfrom: megastructure instance
#
#	ai_weight = {					# scope = country, default = 100
#		modifier = {
#			weight = 0
#			NOT = {
#				has_ethic = ethic_militarist
#			}
#		}
#	}
#
#	construction_blocks_and_blocked_by = none # デフォルトのmulti_stage_typeは、 #コンストラクションがブロックできない、かつ、どのコンストラクションにも ブロックされない場合は、noneを使用する。
#																			#同じタイプのコンストラクションでブロックされた場合、self_typeを使用する。
#																			#建設ブロックや多段式建設でブロックされた場合はmulti_stage_typeを使用します。
#
#	is_ruined_orbital_ring = yes			# default = no
#	scales_with_planet = yes				#default = no
#
#}
