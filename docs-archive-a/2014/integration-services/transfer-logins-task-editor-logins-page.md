---
title: 로그인 전송 태스크 편집기 (로그인 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferloginstask.logins.f1
helpviewer_keywords:
- Transfer Logins Task Editor
ms.assetid: bf244c24-bd45-4ece-b66b-78b488f35c5b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b33fea6c78df75b7eebe8987f952dce33bdc4407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661712"
---
# <a name="transfer-logins-task-editor-logins-page"></a><span data-ttu-id="f71be-102">로그인 전송 태스크 편집기(로그인 페이지)</span><span class="sxs-lookup"><span data-stu-id="f71be-102">Transfer Logins Task Editor (Logins Page)</span></span>
  <span data-ttu-id="f71be-103">**로그인 전송 태스크 편집기** 대화 상자의 **로그인** 페이지를 사용하여 하나 이상의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로그인을 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 한 인스턴스에서 다른 인스턴스로 복사하는 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-103">Use the **Logins** page of the **Transfer Logins Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="f71be-104">이 태스크에 대한 자세한 내용은 [Transfer Logins Task](control-flow/transfer-logins-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f71be-104">For more information about this task, see [Transfer Logins Task](control-flow/transfer-logins-task.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f71be-105">로그인 전송 태스크를 실행하면 대상 서버에 임의의 암호로 로그인이 생성되고 해당 암호는 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-105">When the Transfer Logins task is executed, logins are created on the destination server with random passwords and the passwords are disabled.</span></span> <span data-ttu-id="f71be-106">이러한 로그인을 사용하려면 **sysadmin** 고정 서버 역할의 멤버가 해당 암호를 변경한 다음 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-106">To use these logins, a member of the **sysadmin** fixed server role must change the passwords and then enable them.</span></span> <span data-ttu-id="f71be-107">**sa** 로그인은 전송될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-107">The **sa** login cannot be transferred.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f71be-108">옵션</span><span class="sxs-lookup"><span data-stu-id="f71be-108">Options</span></span>  
 <span data-ttu-id="f71be-109">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="f71be-109">**SourceConnection**</span></span>  
 <span data-ttu-id="f71be-110">목록에서 SMO 연결 관리자를 선택하거나, **\<New connection...>** 을 클릭하여 원본 서버에 대한 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-110">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="f71be-111">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="f71be-111">**DestinationConnection**</span></span>  
 <span data-ttu-id="f71be-112">목록에서 SMO 연결 관리자를 선택하거나, **\<New connection...>** 을 클릭하여 대상 서버에 대한 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-112">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="f71be-113">**LoginsToTransfer**</span><span class="sxs-lookup"><span data-stu-id="f71be-113">**LoginsToTransfer**</span></span>  
 <span data-ttu-id="f71be-114">원본 서버에서 대상 서버로 복사할 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로그인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-114">Select the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins to copy from the source to the destination server.</span></span> <span data-ttu-id="f71be-115">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-115">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="f71be-116">값</span><span class="sxs-lookup"><span data-stu-id="f71be-116">Value</span></span>|<span data-ttu-id="f71be-117">Description</span><span class="sxs-lookup"><span data-stu-id="f71be-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f71be-118">**AllLogins**</span><span class="sxs-lookup"><span data-stu-id="f71be-118">**AllLogins**</span></span>|<span data-ttu-id="f71be-119">원본 서버의 모든 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로그인이 대상 서버로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-119">All [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins on the source server will be copied to the destination server.</span></span>|  
|<span data-ttu-id="f71be-120">**SelectedLogins**</span><span class="sxs-lookup"><span data-stu-id="f71be-120">**SelectedLogins**</span></span>|<span data-ttu-id="f71be-121">**LoginsList** 로 지정된 로그인만 대상 서버로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-121">Only logins specified with **LoginsList** will be copied to the destination server.</span></span>|  
|<span data-ttu-id="f71be-122">**AllLoginsFromSelectedDatabases**</span><span class="sxs-lookup"><span data-stu-id="f71be-122">**AllLoginsFromSelectedDatabases**</span></span>|<span data-ttu-id="f71be-123">**DatabasesList** 로 지정된 데이터베이스의 모든 로그인이 대상 서버로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-123">All logins from the databases specified with **DatabasesList** will be copied to the destination server.</span></span>|  
  
 <span data-ttu-id="f71be-124">**LoginsList**</span><span class="sxs-lookup"><span data-stu-id="f71be-124">**LoginsList**</span></span>  
 <span data-ttu-id="f71be-125">대상 서버로 복사할 원본 서버의 로그인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-125">Select the logins on the source server to be copied to the destination server.</span></span> <span data-ttu-id="f71be-126">이 옵션은 **LoginsToTransfer** 에 대해 **SelectedLogins**를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-126">This option is only available when **SelectedLogins** is selected for **LoginsToTransfer**.</span></span>  
  
 <span data-ttu-id="f71be-127">**DatabasesList**</span><span class="sxs-lookup"><span data-stu-id="f71be-127">**DatabasesList**</span></span>  
 <span data-ttu-id="f71be-128">대상 서버로 복사할 로그인을 포함하는 원본 서버의 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-128">Select the databases on the source server that contain logins to be copied to the destination server.</span></span> <span data-ttu-id="f71be-129">이 옵션은 **LoginsToTransfer** 에 대해 **AllLoginsFromSelectedDatabases**를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-129">This option is only available when **AllLoginsFromSelectedDatabases** is selected for **LoginsToTransfer**.</span></span>  
  
 <span data-ttu-id="f71be-130">**IfObjectExists**</span><span class="sxs-lookup"><span data-stu-id="f71be-130">**IfObjectExists**</span></span>  
 <span data-ttu-id="f71be-131">태스크에서 대상 서버에 이미 있는 로그인과 이름이 동일한 로그인을 처리하는 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-131">Select how the task should handle logins of the same name that already exist on the destination server.</span></span>  
  
 <span data-ttu-id="f71be-132">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-132">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="f71be-133">값</span><span class="sxs-lookup"><span data-stu-id="f71be-133">Value</span></span>|<span data-ttu-id="f71be-134">Description</span><span class="sxs-lookup"><span data-stu-id="f71be-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f71be-135">**FailTask**</span><span class="sxs-lookup"><span data-stu-id="f71be-135">**FailTask**</span></span>|<span data-ttu-id="f71be-136">대상 서버에 이름이 동일한 로그인이 이미 있는 경우 태스크가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-136">Task fails if logins of the same name already exist on the destination server.</span></span>|  
|<span data-ttu-id="f71be-137">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="f71be-137">**Overwrite**</span></span>|<span data-ttu-id="f71be-138">대상 서버에 이름이 동일한 로그인이 있는 경우 이를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-138">Task overwrites logins of the same name on the destination server.</span></span>|  
|<span data-ttu-id="f71be-139">**skip**</span><span class="sxs-lookup"><span data-stu-id="f71be-139">**Skip**</span></span>|<span data-ttu-id="f71be-140">대상 서버에 이름이 동일한 로그인이 있는 경우 이를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-140">Task skips logins of the same name that exist on the destination server.</span></span>|  
  
 <span data-ttu-id="f71be-141">**CopySids**</span><span class="sxs-lookup"><span data-stu-id="f71be-141">**CopySids**</span></span>  
 <span data-ttu-id="f71be-142">로그인에 연결된 보안 식별자를 대상 서버로 복사할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-142">Select whether the security identifiers associated with the logins should be copied to the destination server.</span></span> <span data-ttu-id="f71be-143">로그인 전송 태스크를 데이터베이스 전송 동작과 함께 사용하는 경우에는**CopySids** 를 **True** 로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-143">**CopySids** must be set to **True** if the Transfer Logins task is used along with the Transfer Database task.</span></span> <span data-ttu-id="f71be-144">그렇게 하지 않으면 복사된 로그인을 전송된 데이터베이스에서 인식하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f71be-144">Otherwise, the copied logins will not be recognized by the transferred database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f71be-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f71be-145">See Also</span></span>  
 <span data-ttu-id="f71be-146">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f71be-146">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="f71be-147">[Integration Services 태스크](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="f71be-147">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="f71be-148">[로그인 전송 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="f71be-148">[Transfer Logins Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="f71be-149">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="f71be-149">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="f71be-150">[SMO 연결 관리자](connection-manager/smo-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f71be-150">[SMO Connection Manager](connection-manager/smo-connection-manager.md) </span></span>  
 <span data-ttu-id="f71be-151">[강력한 암호](../relational-databases/security/strong-passwords.md) </span><span class="sxs-lookup"><span data-stu-id="f71be-151">[Strong Passwords](../relational-databases/security/strong-passwords.md) </span></span>  
 [<span data-ttu-id="f71be-152">SQL Server 설치에 대한 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="f71be-152">Security Considerations for a SQL Server Installation</span></span>](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
