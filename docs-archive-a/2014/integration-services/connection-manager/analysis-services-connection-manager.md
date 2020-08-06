---
title: Analysis Services 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], Analysis Services
- connection managers [Integration Services], Analysis Services
- Analysis Services connection manager
ms.assetid: 9f9cadad-a1d0-4db5-98f5-df5dbbec1be4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b5da84acd131b75ef9ea174986836265934fb44b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651226"
---
# <a name="analysis-services-connection-manager"></a><span data-ttu-id="bf02d-102">Analysis Services 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="bf02d-102">Analysis Services Connection Manager</span></span>
  <span data-ttu-id="bf02d-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 연결 관리자를 사용하면 패키지에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 실행하는 서버 또는 큐브 및 차원 데이터에 대한 액세스를 제공하는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf02d-103">An [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager enables a package to connect to a server that runs an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project that provides access to cube and dimension data.</span></span> <span data-ttu-id="bf02d-104">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 패키지를 개발하는 동안에는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]프로젝트에만 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf02d-104">You can only connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project while developing packages in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="bf02d-105">런타임에는 사용자가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트를 배포하는 서버 및 데이터베이스에 패키지가 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf02d-105">At run time, packages connect to the server and the database to which you deployed the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span>  
  
 <span data-ttu-id="bf02d-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 실행 태스크 및 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 처리 태스크와 같은 태스크와 데이터 마이닝 모델 학습 대상과 같은 대상에는 모두 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 연결 관리자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf02d-106">Both tasks, such as the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task and the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task, and destinations, such as the Data Mining Model Training destination, use an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager.</span></span>  
  
 <span data-ttu-id="bf02d-107">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에 대한 자세한 내용은 [다차원 model 데이터베이스&#40;SSAS&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/multidimensional-model-databases-ssas)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf02d-107">For more information about [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases, see [Multidimensional Model Databases &#40;SSAS&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/multidimensional-model-databases-ssas).</span></span>  
  
## <a name="configuration-of-the-analysis-services-connection-manager"></a><span data-ttu-id="bf02d-108">Analysis Services 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="bf02d-108">Configuration of the Analysis Services Connection Manager</span></span>  
 <span data-ttu-id="bf02d-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]패키지에 연결 관리자를 추가 하면에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 런타임에 연결로 확인 되는 연결 관리자를 만들고, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 연결 관리자 속성을 설정 하 고, 연결 관리자를 `Connections` 패키지의 컬렉션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf02d-109">When you add an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that is resolved as an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="bf02d-110">연결 관리자의 `ConnectionManagerType` 속성이 `MSOLAP100`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf02d-110">The `ConnectionManagerType` property of the connection manager is set to `MSOLAP100`.</span></span>  
  
 <span data-ttu-id="bf02d-111">다음과 같은 방법으로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf02d-111">You can configure the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="bf02d-112">Microsoft OLE Provider for Analysis Services 공급자의 요구 사항에 맞게 구성된 연결 문자열을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bf02d-112">Provide a connection string configured to meet the requirements of the Microsoft OLE Provider for Analysis Services provider.</span></span>  
  
-   <span data-ttu-id="bf02d-113">연결할 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스나 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf02d-113">Specify the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project to connect to.</span></span>  
  
-   <span data-ttu-id="bf02d-114">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 연결하는 경우 인증 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf02d-114">If you are connecting to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], specify the authentication mode.</span></span>  
  
-   <span data-ttu-id="bf02d-115">연결 관리자에서 만든 연결이 런타임에 유지될지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf02d-115">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="bf02d-116">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf02d-116">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="bf02d-117">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf02d-117">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topic:</span></span>  
  
-   [<span data-ttu-id="bf02d-118">Analysis Services 연결 관리자 추가 대화 상자 UI 참조</span><span class="sxs-lookup"><span data-stu-id="bf02d-118">Add Analysis Services Connection Manager Dialog Box UI Reference</span></span>](add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 <span data-ttu-id="bf02d-119">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf02d-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
