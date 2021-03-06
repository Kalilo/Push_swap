# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: ggroener <marvin@42.fr>                    +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2016/09/28 11:16:22 by ggroener          #+#    #+#              #
#    Updated: 2016/10/08 10:32:05 by khansman         ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

NAME = push_swap

CFLAGS = -Wall -Wextra -Werror -g -Ofast

CC = gcc

INCLUDES_PATH = includes/

SRCS_PATH = 	srcs/

SRCS_NAME = 	calc_sorted.c				\
				check_dur.c					\
				error_quit.c				\
				is_sorted.c					\
				main.c						\
				pa.c						\
				parse_args.c				\
				pb.c						\
				pre_sort.c					\
				print_a.c					\
				print_b.c					\
				ra.c						\
				rb.c						\
				rr.c						\
				rra.c						\
				rrb.c						\
				rrr.c						\
				sa.c						\
				sb.c						\
				sort.c						\
				sort_3.c					\
				sort_5.c					\
				ss.c						\
				valid_int.c					\

SRCS = $(addprefix $(SRCS_PATH), $(SRCS_NAME))

OBJS_PATH = objs/

OBJS_NAME = $(SRCS_NAME:.c=.o)

OBJS = $(addprefix $(OBJS_PATH), $(OBJS_NAME))

#uncomment these to work on Mac and comment to work on Linux.
LIBRARY = -lmlx -L ../libft/ -lft #-framework OpenGL -framework AppKit

INCLUDES = -I includes/ -I ../libft/includes

#uncomment these to work on Linux and comment to work on Mac.
#LIBRARY = -L /usr/X11/lib -lmlx -lX11 -lm -lXext -L ../libft/ -lft
 
#INCLUDES = -I includes/ -I ../libft/includes -I /usr/X11/include

HEADER = 	$(INCLUDES_PATH)env.h			\
			$(INCLUDES_PATH)includes.h		\
			$(INCLUDES_PATH)prototypes.h	\
			$(INCLUDES_PATH)push_swap.h		\
			$(INCLUDES_PATH)sort.h			\

all: qme odir $(NAME)

define colourecho
	@tput setaf 14
	@echo $1
	@tput sgr0
endef

define colourecho2
	@tput setaf 2
	@echo $1
	@tput sgr0
endef

$(NAME): $(OBJS)
	@Make -C ../libft
	@$(call colourecho, " - Making $(NAME)")
	@clear
	@$(CC) $(CFLAGS) -o $(NAME) $^ $(LIBRARY) $(INCLUDES) -I$(INCLUDES_PATH)
	@clear
	@$(call colourecho, "Make Done!")

$(OBJS_PATH)%.o: $(SRCS_PATH)%.c
	@$(call colourecho, " - Compiling $<")
	@$(CC) $(CFLAGS) $(INCLUDES) -o $@ -c $< -I$(INCLUDES_PATH)
	@$(call colourecho, "Compiling Done!")

odir:
	@mkdir -p $(OBJS_PATH)

clean:
	@Make clean -C ../libft
	@$(call colourecho, " - Clearing object files")
	@rm -f $(OBJS)
	@rm -Rf $(OBJS_PATH)
	@$(call colourecho, "clean done!")

fclean: clean
	@Make fclean -C ../libft
	@$(call colourecho, "Clearing executable files")
	@rm -f $(NAME)
	@$(call colourecho, "fclean done")

re: fclean all
	@$(call colourecho, "re Done!")

format: norme me

norme: norm

norm:
	@clear
	@$(call colourecho2, "Norminette:")
	@norminette $(SRCS)
	@norminette $(HEADER)

qme:
	@if [ ! -f author ]; then \
		whoami > author; \
	fi
	
me: qme
	cat -e author

.PHONY: clean fclean re odir
