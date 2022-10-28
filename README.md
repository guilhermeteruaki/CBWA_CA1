CBWA_CA_1

To run this container.
Using DOcker run:

docker build -t "website name" .

after building the image run the image using command

docker run -it --rm -p 8080:8080 "website name"

Website can be accessed in browser in adress localhost:8080


For security one can select specific IPs that can access the website using the configuration file httpd.conf where you can permit using code A: and deny using prefix D:


REFERENCES
THis docker was created fololowing instructions that can be found inn the following website

https://lipanski.com/posts/smallest-docker-image-static-website

Aditional information was also found in these sources.

https://www.youtube.com/watch?v=4pRo6Ud1JI8&ab_channel=AOSNote

https://www.youtube.com/watch?v=SnSH8Ht3MIc&ab_channel=TechnoTim