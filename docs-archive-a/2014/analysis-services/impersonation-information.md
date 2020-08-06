---
title: 가장 정보 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 42319d60-ccd0-46b8-af0b-f0968c390d8a
author: minewiskan
ms.author: owend
ms.openlocfilehash: f9226fdbe8656aecf0f9173976c67ee386040d6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728924"
---
# <a name="impersonation-information"></a><span data-ttu-id="9a6e3-102">가장 정보</span><span class="sxs-lookup"><span data-stu-id="9a6e3-102">Impersonation Information</span></span>
  <span data-ttu-id="9a6e3-103">**가장 정보** 페이지를 사용하여 Analysis Services에서 데이터 원본에 연결하는 데 사용할 자격 증명을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-103">Use the **Impersonation Information** page to specify the credentials that Analysis Services will use to connect to the data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9a6e3-104">옵션</span><span class="sxs-lookup"><span data-stu-id="9a6e3-104">Options</span></span>  
 <span data-ttu-id="9a6e3-105">**특정 Windows 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="9a6e3-105">**Use a specific Windows user name and password**</span></span>  
 <span data-ttu-id="9a6e3-106">지정된 Windows 사용자 계정의 보안 자격 증명을 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체에 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-106">Select this option to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object use the security credentials of a specified Windows user account.</span></span> <span data-ttu-id="9a6e3-107">지정한 자격 증명은 처리, ROLAP 쿼리, 아웃오브 라인 바인딩, 로컬 큐브, 마이닝 모델, 원격 파티션, 연결된 개체 및 대상과 원본 간의 동기화에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-107">The specified credentials will be used for processing, ROLAP queries, out-of-line bindings, local cubes, mining models, remote partitions, linked objects, and synchronization from target to source.</span></span> <span data-ttu-id="9a6e3-108">그러나 DMX(Data Mining Extensions) OPENQUERY 문의 경우 이 옵션이 무시되고 현재 사용자의 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-108">However, for Data Mining Extensions (DMX) OPENQUERY statements, this option is ignored and the credentials of the current user will be used.</span></span>  
  
 <span data-ttu-id="9a6e3-109">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="9a6e3-109">**User name**</span></span>  
 <span data-ttu-id="9a6e3-110">선택한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체에서 사용할 사용자 계정의 도메인과 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-110">Type the domain and name of the user account to be used by the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="9a6e3-111">이때 다음 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-111">Use the following format:</span></span>  
  
 <span data-ttu-id="9a6e3-112">*\<Domain name>* **\\** *\<User account name>*</span><span class="sxs-lookup"><span data-stu-id="9a6e3-112">*\<Domain name>* **\\** *\<User account name>*</span></span>  
  
 <span data-ttu-id="9a6e3-113">이 옵션은 **특정 사용자 이름 및 암호 사용** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-113">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="9a6e3-114">**암호**</span><span class="sxs-lookup"><span data-stu-id="9a6e3-114">**Password**</span></span>  
 <span data-ttu-id="9a6e3-115">선택한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체에서 사용할 사용자 계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-115">Type the password of the user account to be used by the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="9a6e3-116">이 옵션은 **특정 사용자 이름 및 암호 사용** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-116">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="9a6e3-117">**서비스 계정 사용**</span><span class="sxs-lookup"><span data-stu-id="9a6e3-117">**Use the service account**</span></span>  
 <span data-ttu-id="9a6e3-118">개체를 관리하는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서비스와 연결된 보안 자격 증명을 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체에 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-118">Select this option to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object use the security credentials associated with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] service that manages the object.</span></span> <span data-ttu-id="9a6e3-119">서비스 계정 자격 증명은 처리, ROLAP 쿼리, 원격 파티션, 연결된 개체, 대상과 원본 간의 동기화 등에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-119">The service account credentials will be used for processing, ROLAP queries, remote partitions, linked objects, and synchronization from target to source.</span></span> <span data-ttu-id="9a6e3-120">그러나 DMX(Data Mining Extensions) OPENQUERY 문, 로컬 큐브 및 마이닝 모델의 경우 현재 사용자의 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-120">However, for Data Mining Extensions (DMX) OPENQUERY statements, local cubes, and mining models, the credentials of the current user will be used.</span></span> <span data-ttu-id="9a6e3-121">아웃오브 라인 바인딩에 대해서는 이 옵션이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-121">This option is not supported for out-of-line bindings.</span></span>  
  
 <span data-ttu-id="9a6e3-122">**현재 사용자의 자격 증명 사용**</span><span class="sxs-lookup"><span data-stu-id="9a6e3-122">**Use the credentials of the current user**</span></span>  
 <span data-ttu-id="9a6e3-123">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체에서 아웃오브 라인 바인딩, DMX OPENQUERY, 로컬 큐브 및 마이닝 모델에 대해 현재 사용자의 보안 자격 증명을 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-123">Select this option to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object use the security credentials of the current user for out-of-line bindings, DMX OPENQUERY, local cubes, and mining models.</span></span> <span data-ttu-id="9a6e3-124">처리, ROLAP 쿼리, 원격 파티션, 연결된 개체 및 대상과 원본 간의 동기화에 대해서는 이 옵션이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-124">This option is not supported for processing, ROLAP queries, remote partitions, linked objects, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="9a6e3-125">**계승**</span><span class="sxs-lookup"><span data-stu-id="9a6e3-125">**Inherit**</span></span>  
 <span data-ttu-id="9a6e3-126">데이터베이스 수준에서 정의된 가장 동작을 사용하려면 이 옵션을 선택합니다. 가장 동작은 서버 관리자가 `DataSourceImpersonation` 데이터베이스 속성을 사용하여 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9a6e3-126">Select this option to use the impersonation behavior, defined at the database level, which has been set by the server administrator using the `DataSourceImpersonation` database property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a6e3-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9a6e3-127">See Also</span></span>  
 <span data-ttu-id="9a6e3-128">[다차원 모델의 데이터 원본](multidimensional-models/data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="9a6e3-128">[Data Sources in Multidimensional Models](multidimensional-models/data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="9a6e3-129">SSAS 다차원&#41;&#40;지원 되는 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="9a6e3-129">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
