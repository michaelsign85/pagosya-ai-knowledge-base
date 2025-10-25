---
title: Seguridad y almacenamiento de credenciales bancarias
version: v1
audiencia: merchants
actualizado_en: 2025-10-24
---

PagosYa aplica estándares de seguridad financiera para proteger datos y llaves API de los bancos integrados.

**Políticas principales**
- Las credenciales bancarias se almacenan **cifradas**.
- Acceso bajo principio de **mínimo privilegio**.
- Auditoría de accesos y logs internos.
- Autenticación segura con tokens por usuario.
- Aislamiento de datos por tienda (RLS en Supabase).

**Compromiso**
PagosYa **no accede ni intermedia el dinero** del comercio.  
Las validaciones de pago se realizan directamente con el banco.
