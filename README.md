# pug-learn
Learning the Pug (formerly Jade) templateing system.

## Example Syntax

doctype transitional

html

    include ./head.pug

    body

        div
            p First Paragraph

            p
                | Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
                br
                | Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

            p.
                Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure <i>dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.</i> Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

            p(id="4th",
            class="lorem_ipsum very_import").
                Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

            #2nd_div.lorem_ipsum.very_import
                Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

            ul
                li#bbp_list_item
                    a(href='#') Barry Bonds
                li#bbp_list_item
                    a(href='#') Hank Arron
                li#bbp_list_item
                    a(href='#') Babe Ruth

            ul
                li#hero_list_item: a(href="#") Batman
                li#hero_list_item: a(href="#") Superman
                li#hero_list_item: a(href="#") The Flash

            //- Won't see this comment.
            // Will see this comment.

            - myName = "Jordan"

            p Hello #{myName}

            p 1234 * 5678 = #{1234 * 5678}

            - website = "http://jordanblakey.com"

            a(href="#{website}") New Think Tank

            - heroes = ['Wonder Woman', 'Super Girl', 'Bat Girl']

            ul
                li#hero_list_item: a(href="#") #{heroes[0]}
                li#hero_list_item: a(href="#") #{heroes[1]}
                li#hero_list_item: a(href="#") #{heroes[2]}

            - bq = "blockquote"

            #{bq} A Bad Idea

            - batmanData = "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."

            p= batmanData

            - fnI = {"type": "text", "name": "fName"}

            span First Name
            input(type=fnI.type, name=fnI.name)

            - someInfo = "<i>Very</i>"

            p !{someInfo}

            - date = new Date()
            - hour = date.getHours()

            - if ((hour >= 6) && (hour <= 17)){
                h3 Day Time
            - } else {
                h3 Night Time
            - }

            - age = 18

            if((age >= 16) && (age < 18))
                h3 You can drive.
            else if age >= 18
                h3 You can drive, and vote.
            else
                h3 You can wait until you're 16

            unless age >= 16
                h3 You'll drive at 16
            else
                h3 You can drive

            - dayTime = (((hour >= 6) && (hour <= 17)) ? 'Day Time' : 'Night Time')

            h3 #{dayTime}

            - name = "Sue"

            case name
                when "Sally"
                    h3 Hi Sally
                when "Sue"
                    h3 Hi Sue
                default
                    h3 Hi You

            script.
                console.log('Hello Jade')

            - qbs = ['Palmer', 'Brees', 'Rivers', 'Brady']

            ul
                - for(i=0; i<qbs.length; i++){
                    li= qbs[i]
                - }

            ul
                each qb in qbs
                    li= qb

            - i = 0

            ul
                while i <= 20
                    li= i
                    - i++;

            mixin nflPlayer(name, pos, team)
                li #{name} is the #{pos} for the #{team}

            ul#nflPlayers
                +nflPlayer("Tom", "QB", "Patriots")
                +nflPlayer("Bob", "QB", "Patriots")
                +nflPlayer("Matt", "QB", "Patriots")

            mixin copyr
                | &#169;

            p
                +copyr
                | 2016


            mixin makeList()
                ul
                    - args = Array.prototype.slice.call(arguments);
                    for item in args
                        li= item

            +makeList("Dog", "Cat", "Fish")

            // extends extendex
            // block header
            //    h3 The Title
            //block content
            //    p
            //        | Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

            //block append content2
            //    p
            //        |Appended Data
            //block prepend content 3
            //    p
            //        | I come first
