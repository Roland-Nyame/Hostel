# Nduom University Hostel Backend

Run the API with:

```powershell
npm start
```

Then open `http://localhost:3000`. The service hosts the frontend and API together. Account, room, notification, and report changes persist in a SQLite database.

## Environment configuration

Copy `.env.example` to `.env` and set the values before deployment:

```powershell
Copy-Item .env.example .env
```

`DATABASE_URL` controls the database location. The default `file:./hostel.db` creates a SQLite database inside the `backend` folder. `ADMIN_EMAIL` and `ADMIN_PASSWORD` configure the initial Admin account.

Available endpoints:

- `GET /api/health`
- `POST /api/login`
- `POST /api/register`
- `GET /api/rooms?floor=GF`
- `PATCH /api/rooms/GF-001`

Use the token returned from login in an `Authorization: Bearer <token>` header. Both Admin and Student accounts can read room information; only Admin accounts can update it.

Demo accounts:

- Admin: configured by the hostel office
- Student: index number `10011507`, password `student123`

New registrations always create Student accounts. The hostel office configures Admin access separately.

Example update body:

```json
{ "status": "occupied", "studentNames": ["Ama Mensah", "Kwame Asante"] }
```
