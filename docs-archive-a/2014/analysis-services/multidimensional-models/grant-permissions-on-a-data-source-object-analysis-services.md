---
title: 데이터 원본 개체에 대 한 사용 권한 부여 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.datasources.f1
helpviewer_keywords:
- read/write permissions
- user access rights [Analysis Services], data sources
- security [Analysis Services], data sources
- connection strings [Analysis Services]
- data sources [Analysis Services], security
ms.assetid: b4e302d3-c93b-4383-aa4a-37d15c129830
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0a7de676f5863187c2c137e056392a605af474f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734512"
---
# <a name="grant-permissions-on-a-data-source-object-analysis-services"></a><span data-ttu-id="1e92c-102">데이터 원본 개체에 대한 권한 부여(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="1e92c-102">Grant permissions on a data source object (Analysis Services)</span></span>
  <span data-ttu-id="1e92c-103">일반적으로 대부분의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 사용자는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트의 기반이 되는 데이터 원본에 액세스할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-103">Typically, most users of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] do not require access to the data sources that underlie an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="1e92c-104">사용자는 일반적으로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 내의 데이터를 쿼리하기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-104">Users ordinarily just query the data within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="1e92c-105">그러나 마이닝 모델 기반의 예측을 수행하는 등의 데이터 마이닝 컨텍스트에서는 사용자가 마이닝 모델에서 얻은 데이터와 사용자 제공 데이터를 조인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-105">However, in the context of data mining, such as performing predictions based on a mining model, a user has to join the learned data of a mining model with user-provided data.</span></span> <span data-ttu-id="1e92c-106">사용자 제공 데이터가 포함된 데이터 원본에 연결하기 위해 사용자는 [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery) 또는 [OPENROWSET &#40;DMX&#41;](/sql/dmx/source-data-query-openrowset) 절이 포함된 DMX(Data Mining Extensions) 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-106">To connect to the data source that contains the user-provided data, the user uses a Data Mining Extensions (DMX) query that contains either the [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery) and [OPENROWSET &#40;DMX&#41;](/sql/dmx/source-data-query-openrowset) clause.</span></span>  
  
 <span data-ttu-id="1e92c-107">데이터 원본에 연결하는 DMX 쿼리를 실행하려면 사용자가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 내의 데이터 원본 개체에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-107">To execute a DMX query that connects to a data source, the user must have access to the data source object within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="1e92c-108">기본적으로 서버 관리자 또는 데이터베이스 관리자가 데이터 원본 개체에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-108">By default, only Server Administrators or Database Administrators have access to data source objects.</span></span> <span data-ttu-id="1e92c-109">즉, 관리자가 권한을 부여하지 않으면 사용자는 데이터 원본 개체에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-109">This means that a user cannot access a data source object unless an administrator grants permissions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1e92c-110">보안상의 이유로 OPENROWSET 절에서 열린 연결 문자열을 사용하여 DMX 쿼리를 제출하는 기능은 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-110">For security reasons, the submission of DMX queries by using an open connection string in the OPENROWSET clause is disabled.</span></span>  
  
## <a name="set-read-permissions-to-a-data-source"></a><span data-ttu-id="1e92c-111">데이터 원본에 대한 읽기 권한 설정</span><span class="sxs-lookup"><span data-stu-id="1e92c-111">Set Read permissions to a data source</span></span>  
 <span data-ttu-id="1e92c-112">데이터베이스 역할에는 데이터 원본 개체에 대한 액세스 권한 또는 읽기 권한이 부여되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-112">A database role can be granted either no access permissions on a data source object or read permissions.</span></span>  
  
1.  <span data-ttu-id="1e92c-113">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 연결하고 개체 탐색기에서 해당 데이터베이스에 대한 **역할** 을 확장한 다음 데이터베이스 역할을 클릭하거나 새 데이터베이스 역할을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand **Roles** for the appropriate database in Object explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="1e92c-114">**데이터 원본 액세스** 창의 **데이터 원본** 목록에서 데이터 원본 개체를 찾은 다음 데이터 원본에 대한 **액세스 권한** 목록에서 **읽기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-114">In the **Data Source Access** pane, locate the data source object in the **Data Source** list, and then select the **Read** in the **Access** list for the data source.</span></span> <span data-ttu-id="1e92c-115">이 옵션을 사용할 수 없는 경우 **일반** 창을 확인하여 모든 권한을 선택했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-115">If this option is unavailable, check the **General** pane to see if Full Control is selected.</span></span> <span data-ttu-id="1e92c-116">모든 권한은 이미 권한을 제공하므로, 데이터 원본에 대한 권한을 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-116">Full Control is already providing permission, you cannot override permissions on the data source.</span></span>  
  
## <a name="working-with-the-connection-string-used-by-a-data-source-object"></a><span data-ttu-id="1e92c-117">데이터 원본 개체에서 사용하는 연결 문자열 작업</span><span class="sxs-lookup"><span data-stu-id="1e92c-117">Working With the Connection String Used by a Data Source Object</span></span>  
 <span data-ttu-id="1e92c-118">데이터 원본 개체에는 기본 데이터 원본에 연결하는 데 사용되는 연결 문자열이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-118">The data source object contains the connection string that is used to connect to the underlying data source.</span></span> <span data-ttu-id="1e92c-119">이 연결 문자열을 사용하여 다음 중 하나를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-119">This connection string can specify one of the following:</span></span>  
  
-   <span data-ttu-id="1e92c-120">**사용자 이름 및 암호 지정**</span><span class="sxs-lookup"><span data-stu-id="1e92c-120">**Specify a user name and password**</span></span>  
  
     <span data-ttu-id="1e92c-121">데이터 원본 개체에서 사용하는 연결 문자열이 사용자 이름과 암호를 지정하면 각각 다른 사용자 계정으로 여러 데이터 원본 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-121">If the connection string that a data source object uses specifies a user name and password, you may want to create multiple data source objects, each with different user accounts.</span></span> <span data-ttu-id="1e92c-122">여러 데이터 원본 개체를 만들면 사용자가 특정 데이터 원본 개체에만 액세스할 수 있고 다른 데이터 원본 개체에는 액세스할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-122">Creating multiple data source objects lets users access certain data source objects and prevents those users from accessing other data source objects.</span></span> <span data-ttu-id="1e92c-123">이러한 다른 데이터 원본 개체는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 자체에서 큐브 및 마이닝 모델과 같은 개체를 처리하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-123">These other data source objects can be used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] itself for processing objects, such as cubes and mining models.</span></span>  
  
-   <span data-ttu-id="1e92c-124">**Windows 인증 지정**</span><span class="sxs-lookup"><span data-stu-id="1e92c-124">**Specify Windows Authentication**</span></span>  
  
     <span data-ttu-id="1e92c-125">데이터 원본 개체가 사용하는 연결 문자열이 Windows 인증을 지정하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 클라이언트를 가장할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-125">If the connection string that a data source object uses specifies Windows Authentication, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] must be able to impersonate the client.</span></span> <span data-ttu-id="1e92c-126">데이터 원본이 원격 컴퓨터에 있으면 가장을 위해 두 컴퓨터가 Kerberos 인증을 통해 트러스트되어야 합니다. 그렇지 않은 경우 쿼리는 대개 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-126">If the data source is on a remote computer, the two computers must be trusted for impersonation by using Kerberos authentication, or the query will typically fail.</span></span> <span data-ttu-id="1e92c-127">자세한 내용은 [Configure Analysis Services for Kerberos constrained delegation](../instances/configure-analysis-services-for-kerberos-constrained-delegation.md) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e92c-127">See [Configure Analysis Services for Kerberos constrained delegation](../instances/configure-analysis-services-for-kerberos-constrained-delegation.md) for more information.</span></span>  
  
     <span data-ttu-id="1e92c-128">클라이언트가 OLE DB 및 다른 클라이언트 구성 요소의 가장 수준 속성을 사용한 가장을 허용하지 않으면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 기본 데이터 원본에 대한 익명 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-128">If the client does not allow for impersonation (through the Impersonation Level property in OLE DB and other client components), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will try to make an anonymous connection to the underlying data source.</span></span> <span data-ttu-id="1e92c-129">대부분의 데이터 원본이 익명 연결을 허용하지 않으므로 원격 데이터 원본에 대한 익명 연결은 대개 이뤄지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e92c-129">Anonymous connections to remote data sources rarely succeed, as most data sources do not accept anonymous connections).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e92c-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e92c-130">See Also</span></span>  
 <span data-ttu-id="1e92c-131">[다차원 모델의 데이터 원본](data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="1e92c-131">[Data Sources in Multidimensional Models](data-sources-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="1e92c-132">[연결 문자열 속성 &#40;Analysis Services&#41;](../instances/connection-string-properties-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="1e92c-132">[Connection String Properties &#40;Analysis Services&#41;](../instances/connection-string-properties-analysis-services.md) </span></span>  
 <span data-ttu-id="1e92c-133">[Analysis Services에서 지 원하는 인증 방법](../instances/authentication-methodologies-supported-by-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="1e92c-133">[Authentication methodologies supported by Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md) </span></span>  
 <span data-ttu-id="1e92c-134">[차원 데이터 &#40;Analysis Services&#41;에 대 한 사용자 지정 액세스 권한 부여](grant-custom-access-to-dimension-data-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="1e92c-134">[Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) </span></span>  
 <span data-ttu-id="1e92c-135">[큐브 또는 모델 권한 부여 &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="1e92c-135">[Grant cube or model permissions &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md) </span></span>  
 [<span data-ttu-id="1e92c-136">셀 데이터에 대한 사용자 지정 액세스 권한 부여&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1e92c-136">Grant custom access to cell data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-cell-data-analysis-services.md)  
  
  
