# README

## Niveau Facile
* 1
Album.all.size => 347

* 2
Track.find_by(title:'White Room').artist 
  => "Eric Clapton"

* 3
Track.find_by(duration:188133).title 
  => "Perfect"

* 4
Album.find_by(title:'Use Your Illusion II').artist
 => "Guns N Roses"

## Niveau Moyen
* 1
Album.where("title LIKE '%Great%'").size
   (1.5ms)  SELECT COUNT(*) FROM "albums" WHERE (title LIKE '%Great%')
 => 13 

* 3
Album.where(artist: 'AC/DC').size
   (0.2ms)  SELECT COUNT(*) FROM "albums" WHERE "albums"."artist" = ?  [["artist", "AC/DC"]]
 => 2

* 2
Album.where("title LIKE '%music%'")
  Album Load (0.2ms)  SELECT  "albums".* FROM "albums" WHERE (title LIKE '%music%') LIMIT ?

* 4
Track.where(duration:158589).size
   (0.2ms)  SELECT COUNT(*) FROM "tracks" WHERE "tracks"."duration" = ?  [["duration", 158589]]
 => 0

## Niveau Difficile
* 1
rack.where(artist:'AC/DC').each do |music|
2.7.4 :023 >   puts music.title
2.7.4 :024 > end

* 4
> somme = 0
 => 0 
2.7.4 :030 > Track.where(artist: 'Deep Purple').each do |music|
2.7.4 :031 >   somme += music.price.to_f
2.7.4 :032 > end