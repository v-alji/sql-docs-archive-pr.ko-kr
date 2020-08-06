---
title: 서버 인증 모드 변경 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- sa account
- authentication [SQL Server], changing modes
- server authentication mode [SQL Server]
- modifying server authentication mode
ms.assetid: 79babcf8-19fd-4495-b8eb-453dc575cac0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8bda31ca7d0c5949173a9a3e5ea656c1757c04f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740455"
---
# <a name="change-server-authentication-mode"></a><span data-ttu-id="b5600-102">서버 인증 모드 변경</span><span class="sxs-lookup"><span data-stu-id="b5600-102">Change Server Authentication Mode</span></span>
  <span data-ttu-id="b5600-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 서버 인증 모드를 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-103">This topic describes how to change the server authentication mode in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b5600-104">설치하는 동안 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 은 **Windows 인증 모드** 또는 **SQL Server 및 Windows 인증 모드**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-104">During installation, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] is set to either **Windows Authentication mode** or **SQL Server and Windows Authentication mode**.</span></span> <span data-ttu-id="b5600-105">설치 후 언제든지 인증 모드를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-105">After installation, you can change the authentication mode at any time.</span></span>  
  
 <span data-ttu-id="b5600-106">설치 중에 **Windows 인증 모드** 를 선택하면 sa 로그인이 해제되며 설치 프로그램에서 암호를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-106">If **Windows Authentication mode** is selected during installation, the sa login is disabled and a password is assigned by setup.</span></span> <span data-ttu-id="b5600-107">나중에 인증 모드를 **SQL Server 및 Windows 인증 모드**로 변경해도 sa 로그인은 계속 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-107">If you later change authentication mode to **SQL Server and Windows Authentication mode**, the sa login remains disabled.</span></span> <span data-ttu-id="b5600-108">sa 로그인을 사용하려면 ALTER LOGIN 문을 사용하여 sa 로그인을 설정하고 새 암호를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-108">To use the sa login, use the ALTER LOGIN statement to enable the sa login and assign a new password.</span></span> <span data-ttu-id="b5600-109">sa 로그인은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용한 서버 연결만 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-109">The sa login can only connect to the server by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="b5600-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b5600-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b5600-111">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b5600-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b5600-112">보안</span><span class="sxs-lookup"><span data-stu-id="b5600-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b5600-113">**다음을 사용하여 서버 인증 모드를 변경합니다.**</span><span class="sxs-lookup"><span data-stu-id="b5600-113">**To change server authentication mode, using:**</span></span>  
  
     [<span data-ttu-id="b5600-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b5600-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b5600-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b5600-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b5600-116">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b5600-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b5600-117">보안</span><span class="sxs-lookup"><span data-stu-id="b5600-117">Security</span></span>  
 <span data-ttu-id="b5600-118">sa 계정은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정으로 잘 알려져 있으며 종종 악의적인 사용자의 대상이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-118">The sa account is a well-known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account and it is often targeted by malicious users.</span></span> <span data-ttu-id="b5600-119">애플리케이션에서 요청하지 않는 한 sa 계정을 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="b5600-119">Do not enable the sa account unless your application requires it.</span></span> <span data-ttu-id="b5600-120">sa 로그인에 대해 강력한 암호를 사용하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-120">It is very important that you use a strong password for the sa login.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b5600-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b5600-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-security-authentication-mode"></a><span data-ttu-id="b5600-122">보안 인증 모드를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="b5600-122">To change security authentication mode</span></span>  
  
1.  <span data-ttu-id="b5600-123">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, right-click the server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b5600-124">**보안** 페이지의 **Server 인증**에서 새 서버 인증 모드를 선택한 후에 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-124">On the **Security** page, under **Server authentication**, select the new server authentication mode, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="b5600-125">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 대화 상자에서 **확인** 을 클릭하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-125">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dialog box, click **OK** to acknowledge the requirement to restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="b5600-126">개체 탐색기에서 해당 서버를 마우스 오른쪽 단추로 클릭한 다음 **다시 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-126">In Object Explorer, right-click your server, and then click **Restart**.</span></span> <span data-ttu-id="b5600-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 실행되고 있으면 에이전트도 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-127">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running, it must also be restarted.</span></span>  
  
#### <a name="to-enable-the-sa-login"></a><span data-ttu-id="b5600-128">sa 로그인을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="b5600-128">To enable the sa login</span></span>  
  
1.  <span data-ttu-id="b5600-129">개체 탐색기에서 **보안**, 로그인을 차례로 확장 하 고를 마우스 오른쪽 단추로 클릭 한 `sa` 다음 **속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-129">In Object Explorer, expand **Security**, expand Logins, right-click `sa`, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b5600-130">**일반** 페이지에서 로그인에 대한 암호를 만들고 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-130">On the **General** page, you might have to create and confirm a password for the  login.</span></span>  
  
3.  <span data-ttu-id="b5600-131">**상태** 페이지의 **로그인** 섹션에서 **사용**을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-131">On the **Status** page, in the **Login** section, click **Enabled**, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b5600-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="b5600-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="b5600-133">**sa 로그인을 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="b5600-133">**To enable the sa login**</span></span>  
  
1.  <span data-ttu-id="b5600-134">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-134">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b5600-135">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b5600-136">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b5600-137">다음 예에서는 sa 로그인을 사용하도록 설정하고 새 암호를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b5600-137">The following example enables the sa login and sets a new password.</span></span>  
  
    ```  
    ALTER LOGIN sa ENABLE ;  
    GO  
    ALTER LOGIN sa WITH PASSWORD = '<enterStrongPasswordHere>' ;  
    GO  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b5600-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5600-138">See Also</span></span>  
 <span data-ttu-id="b5600-139">[강력한 암호](../../relational-databases/security/strong-passwords.md) </span><span class="sxs-lookup"><span data-stu-id="b5600-139">[Strong Passwords](../../relational-databases/security/strong-passwords.md) </span></span>  
 <span data-ttu-id="b5600-140">[SQL Server 설치에 대 한 보안 고려 사항](../../sql-server/install/security-considerations-for-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="b5600-140">[Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="b5600-141">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b5600-141">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span></span>  
 [<span data-ttu-id="b5600-142">시스템 관리자가 잠겨 있는 경우 SQL Server에 연결</span><span class="sxs-lookup"><span data-stu-id="b5600-142">Connect to SQL Server When System Administrators Are Locked Out</span></span>](connect-to-sql-server-when-system-administrators-are-locked-out.md)  
  
  
