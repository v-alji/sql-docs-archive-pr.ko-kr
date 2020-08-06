---
title: DataReader 대상 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.datareaderdest.f1
helpviewer_keywords:
- DataReader destination
- destinations [Integration Services], DataReader
ms.assetid: 56fcc4bf-c901-42c3-a71d-110039293431
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 40cfe5d99c33eb19d415f204173005a64bde7855
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742463"
---
# <a name="datareader-destination"></a><span data-ttu-id="ea98e-102">DataReader 대상</span><span class="sxs-lookup"><span data-stu-id="ea98e-102">DataReader Destination</span></span>
  <span data-ttu-id="ea98e-103">DataReader 대상은 ADO.NET `DataReader` 인터페이스를 사용하여 데이터 흐름에 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ea98e-103">The DataReader destination exposes the data in a data flow by using the ADO.NET `DataReader` interface.</span></span> <span data-ttu-id="ea98e-104">그러면 다른 애플리케이션에서 이 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea98e-104">The data can then be consumed by other applications.</span></span> <span data-ttu-id="ea98e-105">예를 들어 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 패키지 실행 결과를 사용하도록 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 보고서의 데이터 원본을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea98e-105">For example, you can configure the data source of a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report to use the result of running a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="ea98e-106">이렇게 하려면 DataReader 대상을 구현하는 데이터 흐름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea98e-106">To do this, you create a data flow that implements the DataReader destination.</span></span>  
  
 <span data-ttu-id="ea98e-107">DataReader 대상의 값을 프로그래밍 방식으로 액세스하고 읽는 방법에 대한 자세한 내용은 [로컬 패키지의 출력 로드](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea98e-107">For information about accessing and reading values in the DataReader destination programmatically, see [Loading the Output of a Local Package](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md).</span></span>  
  
## <a name="configuration-of-the-datareader-destination"></a><span data-ttu-id="ea98e-108">DataReader 대상 구성</span><span class="sxs-lookup"><span data-stu-id="ea98e-108">Configuration of the DataReader Destination</span></span>  
 <span data-ttu-id="ea98e-109">DataReader 대상에 대해 제한 시간 값을 지정하고 제한 시간이 초과될 경우 대상이 실패하는지 여부를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea98e-109">You can specify a time-out value for the DataReader destination and indicate whether the destination should fail if a time-out occurs.</span></span> <span data-ttu-id="ea98e-110">애플리케이션이 지정된 시간 내에 데이터를 요청하지 않으면 제한 시간이 초과됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea98e-110">A time-out occurs if the application does not ask for data within the specified time.</span></span>  
  
 <span data-ttu-id="ea98e-111">DataReader 대상은 하나의 입력을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="ea98e-111">The DataReader destination has one input.</span></span> <span data-ttu-id="ea98e-112">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea98e-112">It does not support an error output.</span></span>  
  
 <span data-ttu-id="ea98e-113">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea98e-113">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="ea98e-114">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="ea98e-114">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ea98e-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="ea98e-115">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="ea98e-116">DataReader 대상 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="ea98e-116">DataReader Destination Custom Properties</span></span>](datareader-destination-custom-properties.md)  
  
 <span data-ttu-id="ea98e-117">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea98e-117">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
