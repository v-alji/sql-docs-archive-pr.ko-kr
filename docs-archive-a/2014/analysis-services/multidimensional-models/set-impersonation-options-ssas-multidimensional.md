---
title: 가장 옵션 설정 (SSAS-다차원) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.impersonationinfo.f1
helpviewer_keywords:
- Impersonation Information dialog box
ms.assetid: 8e127f72-ef23-44ad-81e6-3dd58981770e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b9a8526ff4b8a6dd6f68d13817e427ec70d1953
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653016"
---
# <a name="set-impersonation-options-ssas---multidimensional"></a><span data-ttu-id="003d5-102">가장 옵션 설정(SSAS - 다차원)</span><span class="sxs-lookup"><span data-stu-id="003d5-102">Set Impersonation Options (SSAS - Multidimensional)</span></span>
  <span data-ttu-id="003d5-103">Analysis Services 모델에서 `data source` 개체를 만들 때 구성해야 하는 설정 중 하나는 가장 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-103">When creating a `data source` object in an Analysis Services model, one of the settings that you must configure is an impersonation option.</span></span> <span data-ttu-id="003d5-104">이 옵션은 Analysis Services에서 OLE DB 데이터 공급자를 로드하거나 로밍 프로필을 지원하는 환경에서 사용자 프로필 정보를 분석하는 등 연결과 관련된 로컬 작업을 수행할 때 특정 Windows 사용자 계정의 ID를 가장할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-104">This option determines whether Analysis Services assumes the identity of a specific Windows user account when performing local operations related to the connection, such as loading an OLE DB data provider or resolving user profile information in environments that support roaming profiles.</span></span>  
  
 <span data-ttu-id="003d5-105">Windows 인증을 사용하는 연결의 경우 가장 옵션에 따라 외부 데이터 원본에서 쿼리를 실행할 사용자 ID도 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-105">For connections that use Windows authentication, the impersonation option also determines the user identity under which queries execute on the external data source.</span></span> <span data-ttu-id="003d5-106">예를 들어 가장 옵션을 **contoso\dbuser**로 설정하면 처리 중 데이터를 검색하는 데 사용되는 쿼리가 데이터베이스 서버에서 **contoso\dbuser** 로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-106">For example, if you set the impersonation option to **contoso\dbuser**, queries used to retrieve data during processing will execute as **contoso\dbuser** on the database server.</span></span>  
  
 <span data-ttu-id="003d5-107">이 항목에서는 데이터 원본 개체를 구성할 때 **가장 정보** 대화 상자에서 가장 옵션을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-107">This topic explains how to set impersonation options in the **Impersonation Information** dialog box when configuring a data source object.</span></span>  
  
## <a name="set-impersonation-options-in-sql-server-data-tools"></a><span data-ttu-id="003d5-108">SQL Server Data Tools에서 가장 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="003d5-108">Set impersonation options in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="003d5-109">솔루션 탐색기에서 데이터 원본을 두 번 클릭하여 데이터 원본 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-109">Double-click a data source in Solution Explorer to open Data Source Designer.</span></span>  
  
2.  <span data-ttu-id="003d5-110">데이터 원본 디자이너에서 **가장 정보** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-110">Click the **Impersonation Information** tab in Data Source Designer.</span></span>  
  
3.  <span data-ttu-id="003d5-111">이 항목의 [가장 옵션](#bkmk_options) 에 설명된 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-111">Choose an option described in [Impersonation options](#bkmk_options) in this topic.</span></span>  
  
## <a name="set-impersonation-options-in-management-studio"></a><span data-ttu-id="003d5-112">Management Studio에서 가장 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="003d5-112">Set impersonation options in Management Studio</span></span>  
 <span data-ttu-id="003d5-113">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 다음과 같은 대화 상자의 속성에 대한 줄임표( **...** ) 단추를 클릭하여**가장 정보**대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-113">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open the **Impersonation Information** dialog box by clicking the ellipsis (**...**) button for the following properties of these dialog boxes:</span></span>  
  
-   <span data-ttu-id="003d5-114">**데이터베이스 속성** 대화 상자, 데이터 원본 가장 정보 속성</span><span class="sxs-lookup"><span data-stu-id="003d5-114">**Database Properties** dialog box, through the Data Source Impersonation Info property.</span></span>  
  
-   <span data-ttu-id="003d5-115">**데이터 원본 속성** 대화 상자, 가장 정보 속성</span><span class="sxs-lookup"><span data-stu-id="003d5-115">**Data Source Properties** dialog box, through the Impersonation Info property.</span></span>  
  
-   <span data-ttu-id="003d5-116">**어셈블리 속성** 대화 상자, 가장 정보 속성</span><span class="sxs-lookup"><span data-stu-id="003d5-116">**Assembly Properties** dialog box, through the Impersonation Info property.</span></span>  
  
##  <a name="impersonation-options"></a><a name="bkmk_options"></a> <span data-ttu-id="003d5-117">가장 옵션</span><span class="sxs-lookup"><span data-stu-id="003d5-117">Impersonation options</span></span>  
 <span data-ttu-id="003d5-118">대화 상자에서 모든 옵션을 사용할 수는 있지만 일부 경우에는 일부 옵션이 적절하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-118">All options are available in the dialog box, but not all options are appropriate for every scenario.</span></span> <span data-ttu-id="003d5-119">다음 정보를 사용하여 상황에 가장 적합한 옵션을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="003d5-119">Use the following information to determine the best option for your scenario.</span></span>  
  
 <span data-ttu-id="003d5-120">**특정 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="003d5-120">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="003d5-121">이 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 형식으로 지정 된 Windows 사용자 계정의 보안 자격 증명을 개체에 사용 하려면이 옵션을 선택 *\<Domain name>***\\***\<User account name>* 합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-121">Select this option to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object use the security credentials of a Windows user account specified in this format: *\<Domain name>***\\***\<User account name>*.</span></span>  
  
 <span data-ttu-id="003d5-122">데이터 액세스용으로 특별히 만든 전용, 최소 권한 Windows 사용자 ID를 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-122">Choose this option to use a dedicated, least-privilege Windows user identity that you have created specifically for data access purposes.</span></span> <span data-ttu-id="003d5-123">예를 들어 보고서에 사용되는 데이터를 검색하기 위한 일반 용도의 계정을 정기적으로 만들 경우 여기에서 해당 계정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-123">For example, if you routinely create a general purpose account for retrieving data used in reports, you can specify that account here.</span></span>  
  
 <span data-ttu-id="003d5-124">다차원 데이터베이스의 경우 지정한 자격 증명은 처리, ROLAP 쿼리, 아웃오브 라인 바인딩, 로컬 큐브, 마이닝 모델, 원격 파티션, 연결된 개체 및 대상과 원본 간의 동기화에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-124">For multidimensional databases, the specified credentials will be used for processing, ROLAP queries, out-of-line bindings, local cubes, mining models, remote partitions, linked objects, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="003d5-125">테이블 형식 데이터베이스의 경우 지정한 자격 증명은 처리, 관계형 데이터 저장소에 대해 실행되는 쿼리(DirectQuery 사용), 아웃오브 라인 바인딩, 원격 파티션 및 대상과 원본 간의 동기화에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-125">For tabular databases, the specified credentials will be used for processing, queries that run against a relational data store (using DirectQuery), out-of-line bindings, remote partitions, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="003d5-126">DMX OPENQUERY 문의 경우 이 옵션은 무시되고 지정한 사용자 계정 대신 현재 사용자의 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-126">For DMX OPENQUERY statements, this option is ignored and the credentials of the current user will be used rather than the specified user account.</span></span>  
  
 <span data-ttu-id="003d5-127">**서비스 계정 사용**</span><span class="sxs-lookup"><span data-stu-id="003d5-127">**Use the service account**</span></span>  
 <span data-ttu-id="003d5-128">개체를 관리하는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서비스와 연결된 보안 자격 증명을 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체에 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-128">Select this option to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object use the security credentials associated with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] service that manages the object.</span></span> <span data-ttu-id="003d5-129">기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-129">This is the default option.</span></span> <span data-ttu-id="003d5-130">이전 릴리스에서는 이 옵션이 사용할 수 있는 유일한 옵션이었습니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-130">In previous releases, this was the only option you could use.</span></span> <span data-ttu-id="003d5-131">개별 사용자 계정이 아닌 서비스 수준에서 데이터 액세스를 모니터링하려는 경우 이 옵션을 선호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-131">You might prefer this option to monitor data access at the service level rather than individual user accounts.</span></span>  
  
 <span data-ttu-id="003d5-132">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 경우, 사용 중인 운영 체제에 따라 서비스 계정이 NetworkService이거나 특정 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 대해 만들어진 기본 제공 계정일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-132">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], depending on the operating system you are using, the service account might be NetworkService or a built-in virtual account created for a specific [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="003d5-133">Windows 인증을 사용하는 연결에 대한 서비스 계정을 선택한 경우 이 계정에 대한 데이터베이스 로그인을 만들고 읽기 권한을 부여하십시오. 이 로그인은 처리 중 데이터를 검색하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-133">If you choose the service account for a connection that uses Windows authentication, remember to create a database login for this account and grant read permissions, as it will be used to retrieve data during processing.</span></span> <span data-ttu-id="003d5-134">서비스 계정에 대한 자세한 내용은 [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="003d5-134">For more information about the service account, see [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="003d5-135">데이터베이스 인증을 사용할 때는 서비스가 Analysis Services에 대한 전용 가상 계정으로 실행되는 경우 **서비스 계정 사용** 가장 옵션을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-135">When using database authentication, you should choose the **Use the service account** impersonation option if the service is running under the dedicated virtual account for Analysis Services.</span></span> <span data-ttu-id="003d5-136">이 계정에는 로컬 파일에 액세스할 수 있는 권한이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-136">This account will have permissions to access local files.</span></span> <span data-ttu-id="003d5-137">서비스가 NetworkService로 실행될 경우 더 나은 방법은 **로컬 로그온 허용** 권한을 갖는 최소 권한의 Windows 사용자 계정을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-137">If the service runs as NetworkService, a better alternative is to use a least privilege Windows user account that has **Allow log on locally** permissions.</span></span> <span data-ttu-id="003d5-138">제공하는 계정에 따라 Analysis Services 프로그램 폴더에 대한 파일 액세스 권한을 부여해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-138">Depending on the account you provide, you might also need to grant file access permissions on the Analysis Services program folder.</span></span>  
  
 <span data-ttu-id="003d5-139">다차원 데이터베이스의 경우 서비스 계정 자격 증명은 처리, ROLAP 쿼리, 원격 파티션, 연결된 개체 및 대상과 원본 간의 동기화에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-139">For multidimensional databases, the service account credentials will be used for processing, ROLAP queries, remote partitions, linked objects, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="003d5-140">테이블 형식 데이터베이스의 경우 지정한 자격 증명은 처리, 관계형 데이터 저장소에 대해 실행되는 쿼리(DirectQuery 사용), 원격 파티션 및 대상과 원본 간의 동기화에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-140">For tabular databases, the specified credentials will be used for processing, queries that run against a relational data store (using DirectQuery), remote partitions, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="003d5-141">DMX OPENQUERY 문, 로컬 큐브 및 마이닝 모델의 경우 서비스 계정 옵션을 선택하는 경우에도 현재 사용자의 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-141">For DMX OPENQUERY statements, local cubes, and mining models, the credentials of the current user will be used even if you choose the service account option.</span></span> <span data-ttu-id="003d5-142">아웃오브 라인 바인딩에 대해서는 서비스 계정 옵션이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-142">The service account option is not supported for out-of-line bindings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="003d5-143">서비스 계정에 Analysis Services 인스턴스에 대한 관리자 권한이 없는 경우 큐브에서 데이터 마이닝 모델을 처리할 때 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-143">Errors can occur when processing a data mining model from a cube if the service account does not have administrator permissions on the Analysis Services instance.</span></span> <span data-ttu-id="003d5-144">자세한 내용은 [마이닝 구조: 데이터 원본이 OLAP 큐브인 경우 처리 중 문제](https://go.microsoft.com/fwlink/?LinkId=251610)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="003d5-144">For more information, see [Mining Structure: Issue while Processing when DataSource is OLAP Cube](https://go.microsoft.com/fwlink/?LinkId=251610).</span></span>  
  
 <span data-ttu-id="003d5-145">**현재 사용자의 자격 증명 사용**</span><span class="sxs-lookup"><span data-stu-id="003d5-145">**Use the credentials of the current user**</span></span>  
 <span data-ttu-id="003d5-146">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체에서 아웃오브 라인 바인딩, DMX OPENQUERY, 로컬 큐브 및 마이닝 모델에 대해 현재 사용자의 보안 자격 증명을 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-146">Select this option to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object use the security credentials of the current user for out-of-line bindings, DMX OPENQUERY, local cubes, and mining models.</span></span>  
  
 <span data-ttu-id="003d5-147">테이블 형식 데이터베이스에 대해서는 이 옵션이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-147">This option is not supported for tabular databases.</span></span>  
  
 <span data-ttu-id="003d5-148">로컬 큐브 및 아웃오브 라인 바인딩을 사용하는 처리를 제외하고 이 옵션은 다차원 데이터베이스에 대해 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-148">With the exception of local cubes and processing using out-of-line bindings, this option is not supported for multidimensional databases.</span></span>  
  
 <span data-ttu-id="003d5-149">**기본값** 또는 **상속**</span><span class="sxs-lookup"><span data-stu-id="003d5-149">**Default** or **Inherit**</span></span>  
 <span data-ttu-id="003d5-150">대화 상자에서는 데이터베이스 수준에서 설정된 가장 옵션의 경우 **기본값** 을 사용하고, 데이터 원본 수준에서 설정된 가장 옵션의 경우 **상속** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-150">The dialog box uses **Default** for the impersonation options set at the database level and **Inherit** for impersonation options set at the data source level.</span></span>  
  
 <span data-ttu-id="003d5-151">**데이터 원본-상속 옵션**</span><span class="sxs-lookup"><span data-stu-id="003d5-151">**Data Sources - Inherit Option**</span></span>  
  
 <span data-ttu-id="003d5-152">데이터 원본 수준에서 **상속** 은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 가 부모 개체의 가장 옵션을 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-152">At the data source level, **Inherit** specifies that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] should use the impersonation option of the parent object.</span></span> <span data-ttu-id="003d5-153">다차원 모델에서 부모 개체는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-153">In a multidimensional model, the parent object is the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="003d5-154">**상속** 옵션을 선택하면 이 데이터 원본 및 동일한 데이터베이스의 일부인 다른 데이터 원본의 가장 설정을 중앙에서 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-154">Choosing the **Inherit** option lets you centrally manage the impersonation settings for this and other data sources that are part of the same database.</span></span> <span data-ttu-id="003d5-155">이 옵션이 의미 있는 옵션이 되려면 데이터베이스 수준에서 특정 Windows 사용자 이름 및 암호를 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="003d5-155">For this option to be meaningful, choose a specific Windows user name and password at the database level.</span></span> <span data-ttu-id="003d5-156">그렇지 않으면 데이터 원본의 **상속** 과 데이터베이스의 **기본값** 의 조합이 서비스 계정 옵션을 사용하는 것과 동일하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-156">Otherwise, the combination of **Inherit** on the data source and **Default** on the database are equivalent to using service account option.</span></span>  
  
 <span data-ttu-id="003d5-157">데이터베이스 수준에서 Windows 사용자 이름 및 암호를 지정하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-157">To specify a Windows user name and password at the database level, do the following:</span></span>  
  
1.  <span data-ttu-id="003d5-158">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-158">Right-click the database in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="003d5-159">**데이터 원본 가장 정보**에서 Windows 사용자 이름 및 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-159">In **Data Source Impersonation Info**, specify a Windows user name and password.</span></span>  
  
3.  <span data-ttu-id="003d5-160">각 데이터 원본을 마우스 오른쪽 단추로 클릭한 다음 해당 속성을 보고 각 데이터 원본에서 **상속** 옵션을 사용하고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-160">Right-click each data source and view its properties to ensure that each one is using the **Inherit** option.</span></span>  
  
 <span data-ttu-id="003d5-161">데이터베이스 수준의 기본 설정에 대한 자세한 내용은 [다차원 데이터베이스 속성 설정&#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="003d5-161">For more information about default settings at the database level, see [Set Multidimensional Database Properties &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md).</span></span>  
  
 <span data-ttu-id="003d5-162">**데이터베이스-기본 옵션**</span><span class="sxs-lookup"><span data-stu-id="003d5-162">**Databases - Default option**</span></span>  
  
 <span data-ttu-id="003d5-163">테이블 형식 데이터베이스의 경우 **기본** 은 서비스 계정을 사용함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-163">For tabular databases, **Default** means use the service account.</span></span>  
  
 <span data-ttu-id="003d5-164">다차원 데이터베이스의 경우 **기본값** 은 서비스 계정을 사용하고 데이터 마이닝 작업에 현재 사용자를 사용함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="003d5-164">For multidimensional databases, **Default** means use the service account, and current user for data mining operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="003d5-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="003d5-165">See Also</span></span>  
 <span data-ttu-id="003d5-166">[SSAS 다차원&#41;&#40;데이터 원본 만들기](create-a-data-source-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="003d5-166">[Create a Data Source &#40;SSAS Multidimensional&#41;](create-a-data-source-ssas-multidimensional.md) </span></span>  
 <span data-ttu-id="003d5-167">[SSAS 다차원&#41;&#40;데이터 원본 속성 설정](set-data-source-properties-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="003d5-167">[Set Data Source Properties &#40;SSAS Multidimensional&#41;](set-data-source-properties-ssas-multidimensional.md) </span></span>  
 [<span data-ttu-id="003d5-168">SSAS 테이블 형식&#41;&#40;DirectQuery 배포 시나리오</span><span class="sxs-lookup"><span data-stu-id="003d5-168">DirectQuery Deployment Scenarios &#40;SSAS Tabular&#41;</span></span>](../directquery-deployment-scenarios-ssas-tabular.md)  
  
  
