# Capital-Planning-UsersUSE [CapitalPlanningSystems]
GO

/****** Object:  StoredProcedure [dbo].[spCP_AddOktaUsers]    Script Date: 8/20/2022 4:04:32 PM ******/
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

Create Procedure [dbo].[spCP_AddOktaUsers]
(
    @AddOktaUsersss AddOktaUsersss Readonly
)
As
BEGIN
    IF EXISTS (select UserEmail from Removed_Users rb
		where rb.UserEmail In (select UserEmail from @AddOktaUsersss)	)
    BEGIN
    select UserEmail from  Removed_Users
	Delete tbl From tbl_OktaUsers tbl, Removed_Users rb
	Where tbl.UserEmail= rb.UserEmail

    END
ELSE
    BEGIN
       insert into tbl_OktaUsers(UserID,UserFirstName,UserLastName, UserName, UserEmail)
	select UserID,UserFirstName,UserLastName, UserName, UserEmail
	from @AddOktaUsersss
	where UserID Not In (Select UserID from tbl_OktaUsers)
	
	Update tbl
	set 
	tbl.UserFirstName = tmp.UserFirstName,
	tbl.UserLastName = tmp.UserLastName,
	tbl.UserName = tmp.UserName,
	tbl.UserEmail = tmp.UserEmail
	From tbl_OktaUsers tbl, @AddOktaUsersss tmp
	Where tbl.UserID = tmp.UserID
	PRINT 'New Users Data Inserted'
    END
END
GO
USE [CapitalPlanningSystems]
GO

/****** Object:  StoredProcedure [dbo].[spCP_AddOktaUsers]    Script Date: 8/20/2022 4:04:32 PM ******/
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

Create Procedure [dbo].[spCP_AddOktaUsers]
(
    @AddOktaUsersss AddOktaUsersss Readonly
)
As
BEGIN
    IF EXISTS (select UserEmail from Removed_Users rb
		where rb.UserEmail In (select UserEmail from @AddOktaUsersss)	)
    BEGIN
    select UserEmail from  Removed_Users
	Delete tbl From tbl_OktaUsers tbl, Removed_Users rb
	Where tbl.UserEmail= rb.UserEmail

    END
ELSE
    BEGIN
       insert into tbl_OktaUsers(UserID,UserFirstName,UserLastName, UserName, UserEmail)
	select UserID,UserFirstName,UserLastName, UserName, UserEmail
	from @AddOktaUsersss
	where UserID Not In (Select UserID from tbl_OktaUsers)
	
	Update tbl
	set 
	tbl.UserFirstName = tmp.UserFirstName,
	tbl.UserLastName = tmp.UserLastName,
	tbl.UserName = tmp.UserName,
	tbl.UserEmail = tmp.UserEmail
	From tbl_OktaUsers tbl, @AddOktaUsersss tmp
	Where tbl.UserID = tmp.UserID
	PRINT 'New Users Data Inserted'
    END
END
GO
