---
title: 자격 증명 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- credentials [SQL Server], creating
- authentication [SQL Server], credentials
- logins [SQL Server], credentials
ms.assetid: c1e77e91-2a69-40d9-b8b3-97cffc710586
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 23221424699449ac3775b0e805bb02ae0ad233f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730392"
---
# <a name="create-a-credential"></a><span data-ttu-id="fec95-102">Create a Credential</span><span class="sxs-lookup"><span data-stu-id="fec95-102">Create a Credential</span></span>
  <span data-ttu-id="fec95-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 자격 증명을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-103">This topic describes how to create a credential in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="fec95-104">자격 증명을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증 사용자가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]외부에서 ID를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-104">Credentials provide a way to allow [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication users to have an identity outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fec95-105">자격 증명은 주로 EXTERNAL_ACCESS 권한 집합이 포함된 어셈블리에서 코드를 실행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-105">This is primarily used to execute code in Assemblies with EXTERNAL_ACCESS permission set.</span></span> <span data-ttu-id="fec95-106">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증 사용자가 백업을 저장할 파일 위치와 같은 도메인 리소스에 액세스해야 할 경우에도 자격 증명을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-106">Credentials can also be used when a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication user needs access to a domain resource, such as a file location to store a backup.</span></span>  
  
 <span data-ttu-id="fec95-107">자격 증명은 여러 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인에 동시에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-107">A credential can be mapped to several [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins at the same time.</span></span> <span data-ttu-id="fec95-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인은 한 번에 하나의 자격 증명에만 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-108">A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login can only be mapped to one credential at a time.</span></span> <span data-ttu-id="fec95-109">자격 증명을 만들었으면 **로그인 속성(일반 페이지)** 을 사용하여 로그인을 자격 증명에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-109">After a credential is created, use the **Login Properties (General Page)** to map a login to a credential.</span></span>  
  
 <span data-ttu-id="fec95-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="fec95-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fec95-111">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="fec95-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fec95-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="fec95-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fec95-113">보안</span><span class="sxs-lookup"><span data-stu-id="fec95-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fec95-114">**다음을 사용하여 자격 증명을 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="fec95-114">**To create a credential, using:**</span></span>  
  
     [<span data-ttu-id="fec95-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fec95-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fec95-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fec95-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fec95-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="fec95-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fec95-118">제한 사항</span><span class="sxs-lookup"><span data-stu-id="fec95-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fec95-119">공급자에 대해 매핑된 로그인 자격 증명이 없으면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스 계정에 매핑된 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-119">If there is no login mapped credential for the provider, the credential mapped to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account is used.</span></span>  
  
-   <span data-ttu-id="fec95-120">자격 증명이 고유한 공급자에 대해 사용되는 경우 로그인에 여러 개의 매핑된 자격 증명이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-120">A login can have multiple credentials mapped to it as long as they are used with distinctive providers.</span></span> <span data-ttu-id="fec95-121">로그인별로 각 공급자에 하나의 매핑된 자격 증명만 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-121">There must be only one mapped credential per provider per login.</span></span> <span data-ttu-id="fec95-122">동일한 자격 증명이 다른 로그인에 매핑될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-122">The same credential can be mapped to other logins.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fec95-123">보안</span><span class="sxs-lookup"><span data-stu-id="fec95-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fec95-124">권한</span><span class="sxs-lookup"><span data-stu-id="fec95-124">Permissions</span></span>  
 <span data-ttu-id="fec95-125">자격 증명을 만들거나 수정하려면 ALTER ANY CREDENTIAL 권한이 필요하고 로그인을 자격 증명에 매핑하려면 ALTER ANY LOGIN 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-125">Requires ALTER ANY CREDENTIAL permission to create or modify a credential and ALTER ANY LOGIN permission to map a login to a credential.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fec95-126">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="fec95-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-credential"></a><span data-ttu-id="fec95-127">자격 증명을 만들려면</span><span class="sxs-lookup"><span data-stu-id="fec95-127">To create a credential</span></span>  
  
1.  <span data-ttu-id="fec95-128">개체 탐색기에서 **보안** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-128">In Object Explorer, expand  the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="fec95-129">**자격 증명** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 자격 증명...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-129">Right-click the **Credentials** folder and select **New Credential...**.</span></span>  
  
3.  <span data-ttu-id="fec95-130">**새 자격 증명** 대화 상자의 **자격 증명 이름** 상자에 자격 증명의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-130">In the **New Credential** dialog box, in the **Credential Name** box, type a name for the credential.</span></span>  
  
4.  <span data-ttu-id="fec95-131">**의 컨텍스트를 벗어날 때 나가는 연결에 사용할 계정의 이름을** ID [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]상자에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-131">In the **Identity** box, type the name of the account used for outgoing connections (when leaving the context of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).</span></span> <span data-ttu-id="fec95-132">일반적으로 이 이름은 Windows 사용자 계정이지만 ID는 다른 유형의 계정일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-132">Typically, this will be a Windows user account, but the identity can be an account of another type.</span></span>  
  
     <span data-ttu-id="fec95-133">또는 줄임표 **(…)** 를 클릭하여 **사용자 또는 그룹 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-133">Alternately, click the ellipsis **(...)** to open the **Select User or Group** dialog box.</span></span>  
  
5.  <span data-ttu-id="fec95-134">**암호** 상자와 **암호 확인** 상자에 **ID** 상자에서 지정한 계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-134">In the **Password** and **Confirm password** boxes, type the password of the account specified in the **Identity** box.</span></span> <span data-ttu-id="fec95-135">**ID** 가 Windows 사용자 계정일 경우 이 상자의 내용은 Windows 암호에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-135">If **Identity** is a Windows user account, this is the Windows password.</span></span> <span data-ttu-id="fec95-136">암호가 필요하지 않은 경우 **암호** 를 비워 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-136">The **Password** can be blank, if no password is required.</span></span>  
  
6.  <span data-ttu-id="fec95-137">**암호화 공급자 사용**을 선택하여 EKM(확장 가능 키 관리) 공급자가 자격 증명을 확인하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-137">Select **Use Encryption Provider** to set the credential to be verified by an Extensible Key Management (EKM) Provider.</span></span> <span data-ttu-id="fec95-138">자세한 내용은 [EKM&#40;확장 가능 키 관리&#41;](../encryption/extensible-key-management-ekm.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fec95-138">For more information, see [Extensible Key Management &#40;EKM&#41;](../encryption/extensible-key-management-ekm.md)</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fec95-139">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="fec95-139">Using Transact-SQL</span></span>  
  
###  <a name="to-create-a-credential"></a><a name="Credential"></a><span data-ttu-id="fec95-140">자격 증명을 만들려면</span><span class="sxs-lookup"><span data-stu-id="fec95-140">To create a credential</span></span>  
  
1.  <span data-ttu-id="fec95-141">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fec95-142">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-142">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fec95-143">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fec95-143">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates the credential called "AlterEgo.".   
    -- The credential contains the Windows user "Mary5" and a password.  
    CREATE CREDENTIAL AlterEgo WITH IDENTITY = 'Mary5',   
        SECRET = '<EnterStrongPasswordHere>';  
    GO  
    ```  
  
 <span data-ttu-id="fec95-144">자세한 내용은 [CREATE CREDENTIAL&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fec95-144">For more information, see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).</span></span>  
  
  
