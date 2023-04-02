# BookMyShowDiagram

Table city {
id int [pk]
city_name varchar
}

Table users as U {
user_id int [pk]
full_name varchar
created_at timestamp
mobile_number varchar
}

Table payment {
payment_id varchar [pk]
order_id varchar [ref: - order.order_id]
user_id varchar [ref: > users.user_id]
payment_vendor varchar
payment_vendor_id varchar
payment_status Enum
amount_before_discount int
amount_after_discount int
}

Table order {
order_id varchar [pk]
user_id varchar [ref: > users.user_id]
order_status Enum
show_id varchar
}

Table show {
show_id varchar [pk]
show_start_time int
hall_id varchar [ref: > hall.hall_id]
movie_id varchar [ref: > movie.movie_id]
}

Table seat {
seat_id varchar [pk]
row_no varchar
col_no int
hall_id varchar [ref: > hall.hall_id]
}

Table show_seat {
seat_id varchar [ref: > seat.seat_id]
show_id varchar [ref: > show.show_id]
show_seat_cost varchar
order_id varchar [ref: > order.order_id]
}

Table movie {
movie_id varchar [pk]
duration varchar
movie_name varchar
movie_description varchar
}

Table hall {
hall_id varchar [pk]
hall_name varchar
theater_id varchar [ref: > theatre.theater_id]
}

Table theatre {
theater_id varchar [pk]
city_id varchar [ref: > city.id]
map_url varchar
address varchar
}
