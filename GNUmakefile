#
# Custom Makefile for libavl.  See README.md for usage instructions.
#

BUILD_DIR	?= build
LIBFILE		 = $(BUILD_DIR)/libavl.a
OBJECTS		 = $(BUILD_DIR)/avl.o
AR		?= ar

#
# avl.c includes its own header file as sys/avl.h, and we don't want local
# modifications, so we replicate the header tree under ./include.
#
CPPFLAGS	+= -I include

$(LIBFILE): $(OBJECTS)
	$(AR) rcs $@ $^

$(OBJECTS): $(BUILD_DIR)/%.o: src/%.c include/sys/avl.h include/sys/avl_impl.h | $(BUILD_DIR)
	$(CC) -o $@ -c $(CPPFLAGS) $(CFLAGS) $<

$(BUILD_DIR):
	mkdir -p $@

clean:
	rm -f $(LIBFILE) $(OBJECTS)
