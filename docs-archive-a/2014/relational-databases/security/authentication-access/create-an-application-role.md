---
title: 애플리케이션 역할 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.approle.general.f1
helpviewer_keywords:
- application roles [SQL Server], creating
ms.assetid: 6b8da1f5-3d8e-4f88-b111-b915788b06f1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 51272dad57558cdb771f9b98a2f5e5b3da7609cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653779"
---
# <a name="create-an-application-role"></a><span data-ttu-id="da2e1-102">애플리케이션 역할 만들기</span><span class="sxs-lookup"><span data-stu-id="da2e1-102">Create an Application Role</span></span>
  <span data-ttu-id="da2e1-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 애플리케이션 역할을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-103">This topic describes how to create an application role in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="da2e1-104">애플리케이션 역할은 특정 애플리케이션을 통한 경우를 제외하고 데이터베이스에 대한 사용자 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-104">Application roles restrict user access to a database except through specific applications.</span></span> <span data-ttu-id="da2e1-105">애플리케이션 역할에 사용자가 없으므로 **애플리케이션 역할** 을 선택하면 **역할 멤버** 목록이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-105">Application roles have no users, so the **Role Members** list is not displayed when **Application role** is selected.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="da2e1-106">애플리케이션 역할 암호가 설정된 경우 암호 복잡성이 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-106">Password complexity is checked when application role passwords are set.</span></span> <span data-ttu-id="da2e1-107">애플리케이션 역할을 호출하는 애플리케이션은 해당 암호를 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-107">Applications that invoke application roles must store their passwords.</span></span> <span data-ttu-id="da2e1-108">애플리케이션 역할 암호는 항상 암호화된 상태로 저장되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-108">Application role passwords should always be stored encrypted.</span></span>  
  
 <span data-ttu-id="da2e1-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="da2e1-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="da2e1-110">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="da2e1-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="da2e1-111">보안</span><span class="sxs-lookup"><span data-stu-id="da2e1-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="da2e1-112">**다음을 사용하여 애플리케이션 역할을 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="da2e1-112">**To create an application role, using:**</span></span>  
  
     [<span data-ttu-id="da2e1-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="da2e1-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="da2e1-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="da2e1-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="da2e1-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="da2e1-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="da2e1-116">보안</span><span class="sxs-lookup"><span data-stu-id="da2e1-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="da2e1-117">권한</span><span class="sxs-lookup"><span data-stu-id="da2e1-117">Permissions</span></span>  
 <span data-ttu-id="da2e1-118">데이터베이스에 대한 ALTER ANY APPLICATION ROLE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-118">Requires ALTER ANY APPLICATION ROLE permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="da2e1-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="da2e1-119">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-an-application-role"></a><span data-ttu-id="da2e1-120">애플리케이션 역할을 만들려면</span><span class="sxs-lookup"><span data-stu-id="da2e1-120">To create an application role</span></span>  
  
1.  <span data-ttu-id="da2e1-121">개체 탐색기에서 애플리케이션 역할을 만들 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-121">In Object Explorer, expand the database where you want to create an application role.</span></span>  
  
2.  <span data-ttu-id="da2e1-122">**보안** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-122">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="da2e1-123">**역할** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-123">Expand the **Roles** folder.</span></span>  
  
4.  <span data-ttu-id="da2e1-124">**애플리케이션 역할** 폴더를 마우스 오른쪽 단추로 클릭한 다음, **새 애플리케이션 역할...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-124">Right-click the **Application Roles** folder and select **New Application Role...**.</span></span>  
  
5.  <span data-ttu-id="da2e1-125">**애플리케이션 역할 – 신규** 대화 상자의 **일반 페이지**에서 **역할 이름** 상자에 새 애플리케이션 역할의 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-125">In the **Application Role - New** dialog box, on the **General Page**, enter the new name of the new application role in the **Role name** box.</span></span>  
  
6.  <span data-ttu-id="da2e1-126">**기본 스키마** 상자에 개체 이름을 입력하여 이 역할로 만든 개체를 소유할 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-126">In the **Default Schema** box, specify the schema that will own objects created by this role by entering the object names.</span></span> <span data-ttu-id="da2e1-127">또는 줄임표 **(…)** 를 클릭하여 **스키마 찾기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-127">Alternately, click the ellipsis **(...)** to open the **Locate Schema** dialog box.</span></span>  
  
7.  <span data-ttu-id="da2e1-128">**암호** 상자에 새 역할의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-128">In the **Password** box, enter a password for the new role.</span></span> <span data-ttu-id="da2e1-129">**암호 확인** 상자에 암호를 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-129">Enter that password again into the **Confirm Password** box.</span></span>  
  
8.  <span data-ttu-id="da2e1-130">**이 역할에서 소유한 스키마**에서 이 역할이 소유할 스키마를 선택하거나 봅니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-130">Under **Schemas owned by this role**, select or view schemas that will be owned by this role.</span></span> <span data-ttu-id="da2e1-131">각 스키마는 한 개의 스키마 또는 역할에서만 소유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-131">A schema can be owned by only one schema or role.</span></span>  
  
9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="da2e1-132">추가 옵션</span><span class="sxs-lookup"><span data-stu-id="da2e1-132">Additional Options</span></span>  
 <span data-ttu-id="da2e1-133">**애플리케이션 역할 - 신규** 대화 상자는 또한 **보안 개체** 및 **확장 속성**의 두 추가 페이지에 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-133">The **Application Role - New** dialog box also offers options on two additional pages: **Securables** and **Extended Properties**.</span></span>  
  
-   <span data-ttu-id="da2e1-134">**보안 개체** 페이지에는 사용 가능한 모든 보안 개체와 이러한 보안 개체에서 로그인에 부여할 수 있는 권한이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-134">The **Securables** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span>  
  
-   <span data-ttu-id="da2e1-135">**확장 속성** 페이지에서는 데이터베이스 사용자에 사용자 지정 속성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-135">The **Extended properties** page allows you to add custom properties to database users.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="da2e1-136">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="da2e1-136">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-application-role"></a><span data-ttu-id="da2e1-137">애플리케이션 역할을 만들려면</span><span class="sxs-lookup"><span data-stu-id="da2e1-137">To create an application role</span></span>  
  
1.  <span data-ttu-id="da2e1-138">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-138">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="da2e1-139">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-139">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="da2e1-140">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da2e1-140">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates an application role called "weekly_receipts" that has the password "987Gbv876sPYY5m23" and "Sales" as its default schema.  
  
    CREATE APPLICATION ROLE weekly_receipts   
        WITH PASSWORD = '987G^bv876sPY)Y5m23'   
        , DEFAULT_SCHEMA = Sales;  
    GO  
    ```  
  
 <span data-ttu-id="da2e1-141">자세한 내용은 [CREATE APPLICATION ROLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da2e1-141">For more information, see [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql).</span></span>  
  
  
