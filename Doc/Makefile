.PHONY:    default clean tarball

runme = RunMe

core = Animating Antiban Banking Debug Extras Globals Items Locations \
        Mainloop Manipulation Materials Objects Obstacles Reports Scripts \
        Setup Track Walking

skills = Common Cooking Fishing Magic Mining Money_Making Woodcutting


all:
	@python docgen.py `echo $(runme) | sed -r \
        's/(\w+)/..\/\1.simba/g'` > /dev/null
	@python docgen.py `echo $(core) | sed -r \
        's/(\w+)/..\/MSI\/Core\/\1.simba/g'` > /dev/null
	@python docgen.py `echo $(skills) | sed -r \
        's/(\w+)/..\/MSI\/Skills\/\1.simba/g'` > /dev/null
	@make -C sphinx/ html

clean:
	@rm -f `echo $(core) | sed -r 's/(\w+)/sphinx\/\1.rst/g'`
	@rm -f `echo $(skills) | sed -r 's/(\w+)/sphinx\/\1.rst/g'`
	@make -C sphinx/ clean

tarball:
	@$(MAKE) all
	@tar cjf doc.tar.bz2 -C sphinx/_build/ html
