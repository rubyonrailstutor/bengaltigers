---
layout: post
title:  "build a building"
date:   2014-04-16 12:21:49
categories: ruby objects 
---

today:

1.  build a building
- load the below code into irb
- walkthrough how the objects fit togther
- some kind of small replicant of this

1. begin compiling a vocabulary page
1. add css to the main blog to start getting things to take on a different style
1. do some free association of keywords/vocabulary
1. why did i remove the qualifications from the checklist ? 
1. how to read a diff in git ? 

> git log, git show, git diff


```
class Room
  attr_reader :color, :style, :windows
  attr_writer :color, :style, :windows

  def initialize
    @color = nil
    @style = nil
    @windows = nil
  end

  def paint(color)
    @color = color
  end

  def create(style, windows)
    @style = style
    @windows = windows
  end

  def complete?
    if @style == "corner" && @windows == 2
      return true
    elsif @style == "regular" && @windows == 1
      return true
    else
      return false
    end
  end
end

class Floor 
  attr_accessor :rooms, :capacity

  def initialize(capacity = nil)
    @rooms = []
    @capacity = capacity 
  end

  def complete?
    return unless @capacity
    if @rooms.length == @capacity
      return true
    else
      return false
    end
  end

  def inspect_room(room)
    if room.complete?
      @rooms.push room
      return @rooms
    else
      return nil
    end
  end
end

class Building
  attr_accessor :floors, :height
  def initialize(height = nil)
    @floors = []
    @height = height
  end

  def built?
    return unless @height
    if @floors.count == @height
      return true
    else
      return false
    end
  end

  def add_floor(floor)
    if floor.complete?
      @floors.push floor
      return @floors
    else
      return nil
    end
  end
end
```
