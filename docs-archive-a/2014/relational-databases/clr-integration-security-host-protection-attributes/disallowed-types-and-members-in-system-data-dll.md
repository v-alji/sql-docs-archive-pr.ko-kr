---
title: System.Data.dll에서 허용 되지 않는 형식 및 멤버 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
author: rothja
ms.author: jroth
ms.openlocfilehash: cd62f6f0a90bd167f20a33f8de749acc982f39b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649102"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a><span data-ttu-id="d2730-102">System.Data.dll에 허용되지 않는 유형 및 멤버</span><span class="sxs-lookup"><span data-stu-id="d2730-102">Disallowed Types and Members in System.Data.dll</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="d2730-103">CLR (공용 언어 통합) 프로그래밍에서는,,,,,, `HostProtectionAttribute` `System.Security.Permissions.HostProtectionResource` `ExternalProcessMgmt` `ExternalThreading` `MayLeakOnAbort` `SecurityInfrastructure` `SelfAffectingProcessMgmnt` `SelfAffectingThreading` **sharedstate**, 또는 `Synchronization` `UI` 값을 사용 하 여 열거형을 지정 하는가 있는 형식 또는 멤버를 사용할 때를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2730-103">common language integration (CLR) programming disallows the use of a type or member that has a `HostProtectionAttribute` that specifies a `System.Security.Permissions.HostProtectionResource` enumeration with a value of `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, **SharedState**, `Synchronization`, or `UI`.</span></span> <span data-ttu-id="d2730-104">다음 표에는 HPA(호스트 보호 특성) 값이 허용되지 않는 System.Data.dll 어셈블리의 멤버 및 유형이 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2730-104">The following table lists the members and types of the System.Data.dll assembly whose Host Protection Attribute (HPA) values are disallowed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d2730-105">이 목록은 지원되는 어셈블리에서 생성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d2730-105">This list was generated from the supported assemblies.</span></span> <span data-ttu-id="d2730-106">자세한 내용은 [Supported .NET Framework Libraries](../clr-integration/database-objects/supported-net-framework-libraries.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2730-106">For more information, see [Supported .NET Framework Libraries](../clr-integration/database-objects/supported-net-framework-libraries.md).</span></span>  
  
|<span data-ttu-id="d2730-107">유형 또는 멤버</span><span class="sxs-lookup"><span data-stu-id="d2730-107">Type or Member</span></span>|<span data-ttu-id="d2730-108">HPA 값</span><span class="sxs-lookup"><span data-stu-id="d2730-108">HPA Value(s)</span></span>|  
|--------------------|--------------------|  
|<span data-ttu-id="d2730-109">System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()</span><span class="sxs-lookup"><span data-stu-id="d2730-109">System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()</span></span>|<span data-ttu-id="d2730-110">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="d2730-110">ExternalThreading</span></span>|  
|<span data-ttu-id="d2730-111">System.Data.SqlClient.SqlCommand.BeginExecuteReader()</span><span class="sxs-lookup"><span data-stu-id="d2730-111">System.Data.SqlClient.SqlCommand.BeginExecuteReader()</span></span>|<span data-ttu-id="d2730-112">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="d2730-112">ExternalThreading</span></span>|  
|<span data-ttu-id="d2730-113">System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()</span><span class="sxs-lookup"><span data-stu-id="d2730-113">System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()</span></span>|<span data-ttu-id="d2730-114">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="d2730-114">ExternalThreading</span></span>|  
|<span data-ttu-id="d2730-115">System.Data.SqlClient.SqlDependency..ctor()</span><span class="sxs-lookup"><span data-stu-id="d2730-115">System.Data.SqlClient.SqlDependency..ctor()</span></span>|<span data-ttu-id="d2730-116">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="d2730-116">ExternalThreading</span></span>|  
|<span data-ttu-id="d2730-117">System.Data.SqlClient.SqlDependency.Start()</span><span class="sxs-lookup"><span data-stu-id="d2730-117">System.Data.SqlClient.SqlDependency.Start()</span></span>|<span data-ttu-id="d2730-118">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="d2730-118">ExternalThreading</span></span>|  
|<span data-ttu-id="d2730-119">System.Data.SqlClient.SqlDependency.Stop()</span><span class="sxs-lookup"><span data-stu-id="d2730-119">System.Data.SqlClient.SqlDependency.Stop()</span></span>|<span data-ttu-id="d2730-120">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="d2730-120">ExternalThreading</span></span>|  
|<span data-ttu-id="d2730-121">System.Data.TypedDataSetGenerator</span><span class="sxs-lookup"><span data-stu-id="d2730-121">System.Data.TypedDataSetGenerator</span></span>|<span data-ttu-id="d2730-122">SharedState, Synchronization</span><span class="sxs-lookup"><span data-stu-id="d2730-122">SharedState, Synchronization</span></span>|  
|<span data-ttu-id="d2730-123">System.Xml.XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="d2730-123">System.Xml.XmlDataDocument</span></span>|<span data-ttu-id="d2730-124">동기화</span><span class="sxs-lookup"><span data-stu-id="d2730-124">Synchronization</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2730-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d2730-125">See Also</span></span>  
 <span data-ttu-id="d2730-126">[호스트 보호 특성 및 CLR 통합 프로그래밍](host-protection-attributes-and-clr-integration-programming.md) </span><span class="sxs-lookup"><span data-stu-id="d2730-126">[Host Protection Attributes and CLR Integration Programming](host-protection-attributes-and-clr-integration-programming.md) </span></span>  
 <span data-ttu-id="d2730-127">[Microsoft.VisualBasic.dll에서 허용 되지 않는 형식 및 멤버](disallowed-types-and-members-in-microsoft-visualbasic-dll.md) </span><span class="sxs-lookup"><span data-stu-id="d2730-127">[Disallowed Types and Members in Microsoft.VisualBasic.dll](disallowed-types-and-members-in-microsoft-visualbasic-dll.md) </span></span>  
 <span data-ttu-id="d2730-128">[mscorlib.dll에서 허용 되지 않는 형식 및 멤버](disallowed-types-and-members-in-mscorlib-dll.md) </span><span class="sxs-lookup"><span data-stu-id="d2730-128">[Disallowed Types and Members in mscorlib.dll](disallowed-types-and-members-in-mscorlib-dll.md) </span></span>  
 <span data-ttu-id="d2730-129">[System.dll에서 허용 되지 않는 형식 및 멤버](disallowed-types-and-members-in-system-dll.md) </span><span class="sxs-lookup"><span data-stu-id="d2730-129">[Disallowed Types and Members in System.dll](disallowed-types-and-members-in-system-dll.md) </span></span>  
 [<span data-ttu-id="d2730-130">System.Core.dll에 허용되지 않는 유형 및 멤버</span><span class="sxs-lookup"><span data-stu-id="d2730-130">Disallowed Types and Members in System.Core.dll</span></span>](disallowed-types-and-members-in-system-core-dll.md)  
  
  
