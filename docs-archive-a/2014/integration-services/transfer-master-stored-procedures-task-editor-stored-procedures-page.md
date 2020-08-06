---
title: Master 저장 프로시저 전송 태스크 편집기 (저장 프로시저 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.storedprocedures.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5f9fad408b54d4ef27d4c5d06b0d352f366ad9c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734280"
---
# <a name="transfer-master-stored-procedures-task-editor-stored-procedures-page"></a><span data-ttu-id="433a0-102">master 저장 프로시저 전송 태스크 편집기(저장 프로시저 페이지)</span><span class="sxs-lookup"><span data-stu-id="433a0-102">Transfer Master Stored Procedures Task Editor (Stored Procedures Page)</span></span>
  <span data-ttu-id="433a0-103">**master 저장 프로시저 전송 태스크 편집기** 대화 상자의 **저장 프로시저** 페이지를 사용하여 하나 이상의 사용자 정의 저장 프로시저를 **인스턴스의** master [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스에서 다른 **인스턴스의** master [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]데이터베이스로 복사하기 위한 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-103">Use the **Stored Procedures** page of the **Transfer Master Stored Procedures Task Editor** dialog box to specify properties for copying one or more user-defined stored procedures from the **master** database in one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance to a **master** database in another instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="433a0-104">이 태스크에 대한 자세한 내용은 [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="433a0-104">For more information about this task, see [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="433a0-105">이 태스크는 **dbo** 소유의 사용자 정의 저장 프로시저만 원본 서버의 **master** 데이터베이스에서 대상 서버의 **master** 데이터베이스로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-105">This task transfers only user-defined stored procedures owned by **dbo** from a **master** database on the source server to a **master** database on the destination server.</span></span> <span data-ttu-id="433a0-106">대상 서버의 **master** 데이터베이스에서 CREATE PROCEDURE 권한을 부여받았거나 대상 서버에서 **sysadmin** 고정 서버 역할의 멤버인 사용자만 해당 데이터베이스에 저장 프로시저를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-106">Users must be granted the CREATE PROCEDURE permission in the **master** database on the destination server or be members of the **sysadmin** fixed server role on the destination server to create stored procedures there.</span></span>  
  
## <a name="options"></a><span data-ttu-id="433a0-107">옵션</span><span class="sxs-lookup"><span data-stu-id="433a0-107">Options</span></span>  
 <span data-ttu-id="433a0-108">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="433a0-108">**SourceConnection**</span></span>  
 <span data-ttu-id="433a0-109">목록에서 SMO 연결 관리자를 선택하거나, **\<New connection...>** 을 클릭하여 원본 서버에 대한 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="433a0-110">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="433a0-110">**DestinationConnection**</span></span>  
 <span data-ttu-id="433a0-111">목록에서 SMO 연결 관리자를 선택하거나, **\<New connection...>** 을 클릭하여 대상 서버에 대한 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-111">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="433a0-112">**IfObjectExists**</span><span class="sxs-lookup"><span data-stu-id="433a0-112">**IfObjectExists**</span></span>  
 <span data-ttu-id="433a0-113">대상 서버의 **master** 데이터베이스에 이미 있는 같은 이름의 사용자 정의 저장 프로시저를 태스크에서 처리하는 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-113">Select how the task should handle user-defined stored procedures of the same name that already exist in the **master** database on the destination server.</span></span>  
  
 <span data-ttu-id="433a0-114">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-114">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="433a0-115">값</span><span class="sxs-lookup"><span data-stu-id="433a0-115">Value</span></span>|<span data-ttu-id="433a0-116">Description</span><span class="sxs-lookup"><span data-stu-id="433a0-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="433a0-117">**FailTask**</span><span class="sxs-lookup"><span data-stu-id="433a0-117">**FailTask**</span></span>|<span data-ttu-id="433a0-118">대상 서버의 **master** 데이터베이스에 같은 이름의 저장 프로시저가 이미 있는 경우 태스크가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-118">Task fails if stored procedures of the same name already exist in the **master** database on the destination server.</span></span>|  
|<span data-ttu-id="433a0-119">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="433a0-119">**Overwrite**</span></span>|<span data-ttu-id="433a0-120">대상 서버의 **master** 데이터베이스에 있는 같은 이름의 저장 프로시저를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-120">Task overwrites stored procedures of the same name in the **master** database on the destination server.</span></span>|  
|<span data-ttu-id="433a0-121">**skip**</span><span class="sxs-lookup"><span data-stu-id="433a0-121">**Skip**</span></span>|<span data-ttu-id="433a0-122">대상 서버의 **master** 데이터베이스에 있는 같은 이름의 저장 프로시저를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-122">Task skips stored procedures of the same name that exist in the **master** database on the destination server.</span></span>|  
  
 <span data-ttu-id="433a0-123">**TransferAllStoredProcedures**</span><span class="sxs-lookup"><span data-stu-id="433a0-123">**TransferAllStoredProcedures**</span></span>  
 <span data-ttu-id="433a0-124">원본 서버의 **master** 데이터베이스에 있는 모든 사용자 정의 저장 프로시저를 대상 서버로 복사할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-124">Select whether all user-defined stored procedures in the **master** database on the source server should be copied to the destination server.</span></span>  
  
|<span data-ttu-id="433a0-125">값</span><span class="sxs-lookup"><span data-stu-id="433a0-125">Value</span></span>|<span data-ttu-id="433a0-126">Description</span><span class="sxs-lookup"><span data-stu-id="433a0-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="433a0-127">**True**</span><span class="sxs-lookup"><span data-stu-id="433a0-127">**True**</span></span>|<span data-ttu-id="433a0-128">**master** 데이터베이스의 모든 사용자 정의 저장 프로시저를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-128">Copy all user-defined stored procedures in the **master** database.</span></span>|  
|<span data-ttu-id="433a0-129">**False**</span><span class="sxs-lookup"><span data-stu-id="433a0-129">**False**</span></span>|<span data-ttu-id="433a0-130">지정한 저장 프로시저만 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-130">Copy only the specified stored procedures.</span></span>|  
  
 <span data-ttu-id="433a0-131">**StoredProceduresList**</span><span class="sxs-lookup"><span data-stu-id="433a0-131">**StoredProceduresList**</span></span>  
 <span data-ttu-id="433a0-132">원본 서버의 **master** 데이터베이스에서 대상 **master** 데이터베이스로 복사할 사용자 정의 저장 프로시저를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-132">Select which user-defined stored procedures in the **master** database on the source server should be copied to the destination **master** database.</span></span> <span data-ttu-id="433a0-133">이 옵션은 **TransferAllStoredProcedures** 를 **False**로 설정한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="433a0-133">This option is only available when **TransferAllStoredProcedures** is set to **False**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="433a0-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="433a0-134">See Also</span></span>  
 <span data-ttu-id="433a0-135">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="433a0-135">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="433a0-136">[Integration Services 태스크](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="433a0-136">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="433a0-137">[Master 저장 프로시저 전송 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="433a0-137">[Transfer Master Stored Procedures Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="433a0-138">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="433a0-138">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="433a0-139">SMO 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="433a0-139">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
