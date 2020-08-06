---
title: 저장 프로시저에 대 한 사용 권한 부여 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 01793166-a3e5-4856-8302-21b82d494e69
author: minewiskan
ms.author: owend
ms.openlocfilehash: 13d75ca8b6ff6e7d482e9d69894091518aa9469e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649253"
---
# <a name="grant-permissions-on-stored-procedures-analysis-services"></a><span data-ttu-id="8e894-102">저장 프로시저 관련 사용 권한 부여(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8e894-102">Grant permissions on stored procedures (Analysis Services)</span></span>
  <span data-ttu-id="8e894-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 의 저장 프로시저 또는 어셈블리는 [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET 프로그래밍 언어로 작성된 외부 루틴이며 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]기능을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-103">Stored procedures, or assemblies, in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] are external routines, written in a [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET programming language, that extend the capabilities of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="8e894-104">개발자는 어셈블리를 사용하여 언어 간 통합, 예외 처리, 버전 관리 지원, 배포 지원 및 디버깅 지원을 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-104">Assemblies let the developer take advantage of cross-language integration, exception handling, versioning support, deployment support, and debugging support.</span></span>  
  
 <span data-ttu-id="8e894-105">어셈블리를 등록하려면 서버 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-105">You must be a Server Administrator to register an assembly.</span></span> <span data-ttu-id="8e894-106">[Analysis Services&#41;&#40;서버 관리자 권한 부여 ](instances/grant-server-admin-rights-to-an-analysis-services-instance.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8e894-106">See [Grant Server Administrator Permissions &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md).</span></span>  
  
## <a name="security-context-for-stored-procedure-execution"></a><span data-ttu-id="8e894-107">저장 프로시저 실행을 위한 보안 컨텍스트</span><span class="sxs-lookup"><span data-stu-id="8e894-107">Security context for stored procedure execution</span></span>  
 <span data-ttu-id="8e894-108">모든 사용자가 저장 프로시저를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-108">Any user can call a stored procedure.</span></span> <span data-ttu-id="8e894-109">저장 프로시저 구성에 따라 프로시저를 호출하는 사용자 또는 익명 사용자의 컨텍스트에서 프로시저가 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-109">Depending on how the stored procedure was configured, the procedure can run either in the context of the user calling the procedure or in the context of an anonymous user.</span></span> <span data-ttu-id="8e894-110">익명 사용자에게는 보안 컨텍스트가 없으므로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스 구성에 이 기능을 사용하여 익명 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-110">Because an anonymous user has no security context, use this capability together with configuring the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to permit anonymous access.</span></span>  
  
 <span data-ttu-id="8e894-111">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 저장 프로시저를 실행하기 전에 사용자가 해당 저장 프로시저를 호출하면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 저장 프로시저 내의 동작을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-111">After the user calls a stored procedure but before [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] runs the stored procedure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] evaluates the actions within the stored procedure.</span></span> <span data-ttu-id="8e894-112">이 경우 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서는 사용자에 부여된 사용 권한과 프로시저 실행에 사용되는 권한 집합의 공통 요소를 기준으로 저장 프로시저의 작업을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-112">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] evaluates the actions in a stored procedure based on the intersection of the permissions granted to the user and the permission set used to run the procedure.</span></span> <span data-ttu-id="8e894-113">사용자의 데이터베이스 역할로는 수행할 수 없는 동작이 저장 프로시저에 있는 경우 해당 작업은 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-113">If the stored procedure contains any action that cannot be performed by the database role for the user, that action will not be performed.</span></span>  
  
 <span data-ttu-id="8e894-114">다음은 저장 프로시저 실행에 사용되는 권한 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-114">Following are the permission sets that are used to run stored procedures:</span></span>  
  
-   <span data-ttu-id="8e894-115">**안전** 안전 권한 집합을 사용하면 저장 프로시저에서 [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework의 보호된 리소스에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-115">**Safe** With the Safe permission set, a stored procedure cannot access the protected resources in the [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="8e894-116">이 권한 집합에서는 계산만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-116">This permission set only allows for computations.</span></span> <span data-ttu-id="8e894-117">정보가 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]외부로 누출되지 않고 사용 권한을 승격할 수 없으며 데이터 훼손 공격의 위험이 최소화된다는 점에서 가장 안전한 권한 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-117">This is the safest permission set; information does not leak outside [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], permissions cannot be elevated, and the risk of data tampering attacks is minimized.</span></span>  
  
-   <span data-ttu-id="8e894-118">**외부 액세스** 외부 액세스 권한 집합을 사용하면 저장 프로시저에서 관리 코드를 사용하여 외부 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-118">**External Access** With the External Access permission set, a stored procedure can access external resources by using managed code.</span></span> <span data-ttu-id="8e894-119">저장 프로시저를 이 권한 집합으로 설정하면 서버 불안정을 일으키는 프로그래밍 오류가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-119">Setting a stored procedure to this permission set will not cause programming errors that could lead to server instability.</span></span> <span data-ttu-id="8e894-120">그러나 서버 외부로 정보가 누출되거나 권한 승격 및 데이터 훼손 공격의 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-120">However, this permission set may result in information leaking outside the server, and the possibility of an elevation in permission and data tampering attacks.</span></span>  
  
-   <span data-ttu-id="8e894-121">**제한 없음** 제한 없음 권한 집합을 사용하면 저장 프로시저에서 아무 코드나 사용하여 외부 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-121">**Unrestricted** With the Unrestricted permission set, a stored procedure can access external resources by using any code.</span></span> <span data-ttu-id="8e894-122">저장 프로시저를 이 권한 집합으로 설정하면 저장 프로시저의 보안이나 안정성이 보장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e894-122">With this permission set, there are no security or reliability guarantees for stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e894-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e894-123">See Also</span></span>  
 [<span data-ttu-id="8e894-124">다차원 모델 어셈블리 관리</span><span class="sxs-lookup"><span data-stu-id="8e894-124">Multidimensional Model Assemblies Management</span></span>](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
