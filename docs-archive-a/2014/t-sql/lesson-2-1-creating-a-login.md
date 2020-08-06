---
title: 로그인 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- creating a login
ms.assetid: a2512310-bdb6-41dc-858a-e866b2b58afc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 400a57693fbea10270a51f5735a19b9639112ce9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737354"
---
# <a name="creating-a-login"></a><span data-ttu-id="ee0cd-102">로그인 만들기</span><span class="sxs-lookup"><span data-stu-id="ee0cd-102">Creating a Login</span></span>
  <span data-ttu-id="ee0cd-103">[!INCLUDE[ssDE](../includes/ssde-md.md)]에 액세스하려면 사용자는 로그인이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-103">To access the [!INCLUDE[ssDE](../includes/ssde-md.md)], users require a login.</span></span> <span data-ttu-id="ee0cd-104">로그인은 사용자의 ID를 Windows 계정 또는 Windows 그룹의 멤버로 나타내거나 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에만 존재하는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]로그인이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-104">The login can represent the user's identity as a Windows account or as a member of a Windows group, or the login can be a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login that exists only in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ee0cd-105">가능하면 Windows 인증을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-105">Whenever possible you should use Windows Authentication.</span></span>  
  
 <span data-ttu-id="ee0cd-106">기본적으로 컴퓨터의 관리자는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 대한 모든 액세스 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-106">By default, administrators on your computer have full access to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ee0cd-107">따라서 낮은 권한의 사용자가 필요할 것이므로 컴퓨터에서 새로운 로컬 Windows 인증 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-107">For this lesson, we want to have a less privileged user; therefore, you will create a new local Windows Authentication account on your computer.</span></span> <span data-ttu-id="ee0cd-108">이 작업을 수행하려면 컴퓨터의 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-108">To do this, you must be an administrator on your computer.</span></span> <span data-ttu-id="ee0cd-109">그런 다음 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 대한 액세스 권한을 새 사용자에게 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-109">Then you will grant that new user access to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-create-a-new-windows-account"></a><span data-ttu-id="ee0cd-110">새 Windows 계정을 만들려면</span><span class="sxs-lookup"><span data-stu-id="ee0cd-110">To create a new Windows account</span></span>  
  
1.  <span data-ttu-id="ee0cd-111">**시작**, **실행**을 차례로 클릭 하 고 **열기** 상자에를 입력 한 `%SystemRoot%\system32\compmgmt.msc /s` 다음 **확인** 을 클릭 하 여 컴퓨터 관리 프로그램을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-111">Click **Start**, click **Run**, in the **Open** box, type `%SystemRoot%\system32\compmgmt.msc /s`, and then click **OK** to open the Computer Management program.</span></span>  
  
2.  <span data-ttu-id="ee0cd-112">**시스템 도구**에서 **로컬 사용자 및 그룹**을 확장하고 **사용자**를 마우스 오른쪽 단추로 클릭한 다음 **새 사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-112">Under **System Tools**, expand **Local Users and Groups**, right-click **Users**, and then click **New User**.</span></span>  
  
3.  <span data-ttu-id="ee0cd-113">**사용자 이름** 상자에 **Mary**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-113">In the **User name** box type **Mary**.</span></span>  
  
4.  <span data-ttu-id="ee0cd-114">**암호** 및 **암호 확인** 상자에 강력한 암호를 입력한 다음 **만들기** 를 클릭하여 새 로컬 Windows 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-114">In the **Password** and **Confirm password** box, type a strong password, and then click **Create** to create a new local Windows user.</span></span>  
  
### <a name="to-create-a-login"></a><span data-ttu-id="ee0cd-115">로그인을 만들려면</span><span class="sxs-lookup"><span data-stu-id="ee0cd-115">To create a login</span></span>  
  
1.  <span data-ttu-id="ee0cd-116">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 쿼리 편집기 창에서 `computer_name` 을 컴퓨터 이름으로 바꾸어서 다음 코드를 입력하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-116">In a Query Editor window of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], type and execute the following code replacing `computer_name` with the name of your computer.</span></span> <span data-ttu-id="ee0cd-117">`FROM WINDOWS` 는 Windows가 사용자를 인증한다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-117">`FROM WINDOWS` indicates that Windows will authenticate the user.</span></span> <span data-ttu-id="ee0cd-118">사용자의 연결 문자열에서 다른 데이터베이스를 나타내지 않는 경우 선택적 `DEFAULT_DATABASE` 인수는 `Mary` 를 `TestData` 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-118">The optional `DEFAULT_DATABASE` argument connects `Mary` to the `TestData` database, unless her connection string indicates another database.</span></span> <span data-ttu-id="ee0cd-119">이 문에서는 [!INCLUDE[tsql](../includes/tsql-md.md)] 문을 종료하기 위한 선택적 문자로 세미콜론이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-119">This statement introduces the semicolon as an optional termination for a [!INCLUDE[tsql](../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    CREATE LOGIN [computer_name\Mary]  
        FROM WINDOWS  
        WITH DEFAULT_DATABASE = [TestData];  
    GO  
    ```  
  
     <span data-ttu-id="ee0cd-120">이 코드는 컴퓨터가 인증하는 사용자 이름 `Mary`에게 이 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 액세스할 수 있는 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-120">This authorizes a user name `Mary`, authenticated by your computer, to access this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ee0cd-121">컴퓨터에 둘 이상의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스가 있을 경우 `Mary` 가 액세스해야 하는 각 인스턴스에서 로그인을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-121">If there is more than one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the computer, you must create the login on each instance that `Mary` must access.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ee0cd-122">`Mary` 가 도메인 계정이 아니므로 이 사용자 이름은 이 컴퓨터에서만 인증될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee0cd-122">Because `Mary` is not a domain account, this user name can only be authenticated on this computer.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ee0cd-123">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="ee0cd-123">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ee0cd-124">데이터베이스에 대한 액세스 권한 부여</span><span class="sxs-lookup"><span data-stu-id="ee0cd-124">Granting Access to a Database</span></span>](lesson-2-2-granting-access-to-a-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="ee0cd-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ee0cd-125">See Also</span></span>  
 <span data-ttu-id="ee0cd-126">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ee0cd-126">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span></span>  
 [<span data-ttu-id="ee0cd-127">인증 모드 선택</span><span class="sxs-lookup"><span data-stu-id="ee0cd-127">Choose an Authentication Mode</span></span>](../relational-databases/security/choose-an-authentication-mode.md)  
  
  
