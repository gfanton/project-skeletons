#**************************************************************************#
#                                                                          #
#                                                        :::      :::::::: #
#   Makefile                                           :+:      :+:    :+: #
#                                                    +:+ +:+         +:+   #
#   By: world42 <world42@student.42.fr>            +#+  +:+       +#+      #
#                                                +#+#+#+#+#+   +#+         #
#   Created: 2014/02/24 19:53:30 by world42           #+#    #+#           #
#   Updated: 2014/02/24 20:52:06 by world42          ###   ########.fr     #
#                                                                          #
#**************************************************************************#


NAME = __PROJECT-NAME__
LIB_USER = ft
LIB_DYNAMIQUE =
LIB_PATH =
C = \033[0;35m
NORME = norminette
CFLAGS = -Wall -Werror -Wextra
SRCPATH = ./srcs/
INCLUDES = ./includes/ ./libft/includes/
SRCS = main.c __PROJECT-NAME__.c

V = 0
G = 0
N = 0
SILENCE_1 :=
SILENCE_0 :=@
SKIP_1 :=
SKIP_0 := \033[A
NORC_1 := norme
NORC_0 :=
DEBUG_1 := -g
DEBUG_0 :=
STAT = $(STAT_$(S))
SKIP = $(SKIP_$(V))
DEBUG = $(DEBUG_$(G))
SILENCE = $(SILENCE_$(V))
NORC = $(NORC_$(N))
MYLIB = $(addprefix lib, $(LIB_USER))
ALLIB = $(addprefix -l, $(LIB_DYNAMIQUE)) $(addprefix -l, $(LIB_USER))
INCLUDE = $(addprefix -I, $(INCLUDES))
LIB = $(addprefix -L, $(LIB_PATH)) $(addprefix -L./, $(MYLIB)) $(ALLIB)
CC = $(SILENCE)gcc
RM = $(SILENCE)rm -rf
MAKE = $(SILENCE)make V=$(V) G=$(G) S=$(S) N=$(N)
SRC = $(addprefix $(SRCPATH), $(SRCS))
OBJS = $(SRC:.c=.o)
NORMESRC = $(SRC:.c)
LIBALL = $(addprefix -C, $(MYLIB))
STATS = .makefile_stat
U = $(C)[$(NAME)]----->\033[0m

all: $(NORC) liball $(NAME) $(STAT)

$(NAME): $(OBJS)
	@echo "$(U)$(C)[COMPILE:\033[1;32m DONE$(C)]\033[0m"
	@echo "$(U)$(C)[BUILD]\033[0;32m"
	$(CC) -o $(NAME) $(OBJS) $(DEBUG) $(CFLAGS) $(INCLUDE) $(LIB)
	@echo "$(SKIP)\033[2K"
	@echo "$(SKIP)$(U)$(C)[BUILD  :\033[1;32m DONE$(C)]\033[0m"

.c.o:
	@echo "$(U)$(C)[COMPILE: \033[1;31m$<\033[A\033[0m"
	@echo "\033[0;32m"
	$(CC) -o $@ $(DEBUG) $(CFLAGS) $(INCLUDE) -c $<
	@echo "\033[1;31m [.working.]"
	@echo "$(SKIP)\033[2K\033[A\033[2K$(SKIP)"

.clean:
	@echo "$(U)$(C)[CLEAN]\033[0;32m"
	$(RM) $(OBJS)
	@echo "$(SKIP)$(U)$(C)[CLEAN:\033[1;32m   DONE$(C)]\033[0m"

clean: libclean .clean

fclean: libfclean .clean
	@echo "$(U)$(C)[F-CLEAN]\033[0;32m"
	$(RM) $(NAME)
	@echo "$(SKIP)$(U)$(C)[F-CLEAN:\033[1;32m DONE$(C)]\033[0m"

liball: LIBARG = all
liball: $(LIBALL)

libclean: LIBARG = clean
libclean: $(LIBALL)

libfclean: LIBARG = fclean
libfclean: $(LIBALL)

libre: LIBARG = re
libre: $(LIBALL)

$(LIBALL):
	$(MAKE) $(LIBARG) $@

norme:
	@echo "$(U)$(C)[NORME]\033[0;32m"
	@echo "\033[6;31mchecking srcs:\033[0;32m"
	$(SILENCE)$(NORME) $(SRC)
	@echo "\033[6;31mchecking header:\033[0;32m"
	$(SILENCE)$(NORME) $(NINCLUDE)
	@echo "$(U)$(C)[NORME:\033[1;32m DONE$(C)]\033[0m"

re: libre fclean all

.PHONY: clean .clean fclean
