# Cytoscape.Font.svg

#!/usr/bin/perl

use strict;
use warnings;
use Getopt::Std;


sub usage{
	print STDOUT "usage: $0  <option> <value>...\n";
	print STDOUT "Options\n";
	print STDOUT "\t-i : original SVG file, required\n";
}

our($opt_i);
getopts('i:');

&usage unless $opt_i;

if($opt_i){
open (I,"$opt_i");
open (O,">xx.svg");
while(<I>){
		if ($_ =~ s/(font-family="')ArialMT(.*)_/$1Arial-ItalicMT$2\ /){
		if(/sp\./){
			s/(font-family="')Arial-ItalicMT/$1Arial/;
			s|>(.*) sp.|><tspan style="font-style: italic;">$1</tspan> sp.|;
			print O "$_";
		}else{
				print O "$_";
				}
	}else{
		print O "$_"}
}

close O;
close I;
}
