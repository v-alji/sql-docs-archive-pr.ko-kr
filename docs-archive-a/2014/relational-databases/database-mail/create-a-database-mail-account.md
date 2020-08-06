---
title: 데이터베이스 메일 계정 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], accounts
- accounts [Database Mail]
ms.assetid: c07abbc6-fc6a-470b-8fa3-532f2e06b16a
author: stevestein
ms.author: sstein
ms.openlocfilehash: ec7d1c9147998b5a19cc0e6af13220bd64e165fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649098"
---
# <a name="create-a-database-mail-account"></a><span data-ttu-id="aa86f-102">데이터베이스 메일 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="aa86f-102">Create a Database Mail Account</span></span>
  <span data-ttu-id="aa86f-103">**데이터베이스 메일 구성 마법사** 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 을 사용하여 데이터베이스 메일 계정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-103">Use either the **Database Mail Configuration Wizard** or [!INCLUDE[tsql](../../includes/tsql-md.md)] to create a Database Mail account.</span></span>  
  
-   <span data-ttu-id="aa86f-104">**시작하기 전 주의 사항:**  [필수 구성 요소](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="aa86f-104">**Before you begin:**  [Prerequisites](#Prerequisites)</span></span>  
  
-   <span data-ttu-id="aa86f-105">**다음을 사용하여 데이터베이스 메일 계정 만들기:**  [데이터베이스 메일 구성 마법사](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="aa86f-105">**To Create a Database Mail Account, using:**  [Database Mail Configuration Wizard](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
-   <span data-ttu-id="aa86f-106">**후속 작업:**  [데이터베이스 메일을 구성하기 위한 다음 단계](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="aa86f-106">**Follow Up:**  [Next Steps to Configure the Database Mail](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="aa86f-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="aa86f-107">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="aa86f-108">필수 조건</span><span class="sxs-lookup"><span data-stu-id="aa86f-108">Prerequisites</span></span>  
  
-   <span data-ttu-id="aa86f-109">전자 메일을 보내는 데 사용할 SMTP(Simple Mail Transfer Protocol) 서버의 이름과 포트 번호를 결정합니다. SMTP 서버에 인증이 필요한 경우 SMTP 서버의 사용자 이름과 암호를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-109">Determine the server name and port number for the Simple Mail Transfer Protocol (SMTP) server you use to send e-mail.If the SMTP server requires authentication, determine the user name and password for the SMTP server.</span></span>  
  
-   <span data-ttu-id="aa86f-110">필요에 따라 서버의 유형과 포트 번호도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-110">Optionally, you may also specify the type of the server and the port number for the server.</span></span> <span data-ttu-id="aa86f-111">보내는 메일의 서버 유형은 항상 'SMTP'입니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-111">The server type is always 'SMTP' for outgoing mail.</span></span> <span data-ttu-id="aa86f-112">대부분의 SMTP 서버에서는 기본값인 포트 25를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-112">Most SMTP servers use port 25, the default.</span></span>  
  
##  <a name="using-database-mail-configuration-wizard"></a><a name="SSMSProcedure"></a> <span data-ttu-id="aa86f-113">데이터베이스 메일 구성 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="aa86f-113">Using Database Mail Configuration Wizard</span></span>  
 <span data-ttu-id="aa86f-114">**마법사를 사용하여 데이터베이스 메일 계정을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="aa86f-114">**To create a Database Mail account using a Wizard**</span></span>  
  
-   <span data-ttu-id="aa86f-115">개체 탐색기에서 데이터베이스 메일을 구성할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결한 다음 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-115">In Object Explorer, connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to configure Database Mail on, and expand the server tree.</span></span>  
  
-   <span data-ttu-id="aa86f-116">**관리** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-116">Expand the **Management** node</span></span>  
  
-   <span data-ttu-id="aa86f-117">데이터베이스 메일을 두 번 클릭하여 데이터베이스 메일 구성 마법사를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-117">Double Click Database Mail to open the Database Mail Configuration Wizard.</span></span>  
  
-   <span data-ttu-id="aa86f-118">**구성 태스크 선택** 페이지에서 **데이터베이스 메일 계정 및 프로필 관리**를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-118">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles**, and click **Next**.</span></span>  
  
-   <span data-ttu-id="aa86f-119">**프로필 및 계정 관리** 페이지에서 **새 계정 만들기** 를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-119">On the **Manage Profiles and Accounts** page, select **Create a new account** and click **Next**.</span></span>  
  
-   <span data-ttu-id="aa86f-120">**새 계정** 페이지에서 계정 이름, 설명, 메일 서버 정보 및 인증 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-120">On the **New Account** page, specify the account name, description, mail server information, and authentication type.</span></span> <span data-ttu-id="aa86f-121">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-121">Click **Next**</span></span>  
  
-   <span data-ttu-id="aa86f-122">**마법사 완료** 페이지에서 수행할 동작을 검토하고 **마침** 을 클릭하여 새 계정 만들기를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-122">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete creating the new account.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="aa86f-123">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="aa86f-123">Using Transact-SQL</span></span>  
 <span data-ttu-id="aa86f-124">**Transact-SQL을 사용하여 데이터베이스 메일 계정을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="aa86f-124">**To Create a Database Mail account using Transact-SQL**</span></span>  
  
 <span data-ttu-id="aa86f-125">**msdb.dbo.sysmail_add_account_sp** 저장 프로시저를 실행하여 계정을 만들고 다음 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-125">Execute the stored procedure **msdb.dbo.sysmail_add_account_sp** to create the account and specify the following information:</span></span>  
  
-   <span data-ttu-id="aa86f-126">만들 계정의 이름</span><span class="sxs-lookup"><span data-stu-id="aa86f-126">The name of the account to create.</span></span>  
  
-   <span data-ttu-id="aa86f-127">계정에 대한 설명(옵션)</span><span class="sxs-lookup"><span data-stu-id="aa86f-127">An optional description of the account.</span></span>  
  
-   <span data-ttu-id="aa86f-128">보내는 전자 메일 메시지에 표시할 전자 메일 주소</span><span class="sxs-lookup"><span data-stu-id="aa86f-128">The e-mail address to show on outgoing e-mail messages.</span></span>  
  
-   <span data-ttu-id="aa86f-129">보내는 전자 메일 메시지에 표시할 표시 이름</span><span class="sxs-lookup"><span data-stu-id="aa86f-129">The display name to show on outgoing e-mail messages.</span></span>  
  
-   <span data-ttu-id="aa86f-130">SMTP 서버의 이름</span><span class="sxs-lookup"><span data-stu-id="aa86f-130">The server name of the SMTP server.</span></span>  
  
-   <span data-ttu-id="aa86f-131">SMTP 서버에 인증이 필요한 경우 SMTP 서버에 로그온하는 데 사용할 사용자 이름</span><span class="sxs-lookup"><span data-stu-id="aa86f-131">The user name to use to log on to the SMTP server, if the SMTP server requires authentication.</span></span>  
  
-   <span data-ttu-id="aa86f-132">SMTP 서버에 인증이 필요한 경우 SMTP 서버에 로그온하는 데 사용할 암호</span><span class="sxs-lookup"><span data-stu-id="aa86f-132">The password to use to log on to the SMTP server, if the SMTP server requires authentication.</span></span>  
  
 <span data-ttu-id="aa86f-133">다음 예에서는 새 데이터베이스 메일 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aa86f-133">The following example creates a new Database Mail account.</span></span>  
  
```  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
```  
  
##  <a name="follow-up-next-steps-to-configuring-the-database-mail"></a><a name="FollowUp"></a> <span data-ttu-id="aa86f-134">후속 작업: 데이터베이스 메일을 구성하기 위한 다음 단계</span><span class="sxs-lookup"><span data-stu-id="aa86f-134">Follow Up: Next Steps to Configuring the Database Mail</span></span>  
  
-   [<span data-ttu-id="aa86f-135">데이터베이스 메일 프로필 만들기</span><span class="sxs-lookup"><span data-stu-id="aa86f-135">Create a Database Mail Profile</span></span>](create-a-database-mail-profile.md)  
  
  
