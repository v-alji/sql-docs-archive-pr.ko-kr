---
title: 데이터 처리 확장 프로그램 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- data sources [Reporting Services], data processing extensions
- data processing extensions [Reporting Services]
- extensions [Reporting Services], data processing
ms.assetid: 8dc2b44e-5ad9-411d-a29f-7213e29321a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5a1b7668f2319e742dcf3f1969fc3c5cc85cd7eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741591"
---
# <a name="implementing-a-data-processing-extension"></a><span data-ttu-id="cdad4-102">데이터 처리 확장 프로그램 구현</span><span class="sxs-lookup"><span data-stu-id="cdad4-102">Implementing a Data Processing Extension</span></span>
  <span data-ttu-id="cdad4-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 데이터 처리 확장 프로그램을 통해 데이터 원본에 연결하고 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdad4-103">Data processing extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enable you to connect to a data source and retrieve data.</span></span> <span data-ttu-id="cdad4-104">이 프로그램은 데이터 원본과 데이터 세트을 연결하는 역할도 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdad4-104">They also serve as a bridge between a data source and a dataset.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="cdad4-105">데이터 처리 확장 프로그램은 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 데이터 공급자 인터페이스의 하위 집합을 본떠서 만든 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cdad4-105">data processing extensions are modeled after a subset of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider interfaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cdad4-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="cdad4-106">In This Section</span></span>  
 [<span data-ttu-id="cdad4-107">데이터 처리 확장 프로그램 개요</span><span class="sxs-lookup"><span data-stu-id="cdad4-107">Data Processing Extensions Overview</span></span>](data-processing-extensions-overview.md)  
 <span data-ttu-id="cdad4-108">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]용 사용자 지정 데이터 처리 확장 프로그램을 작성하는 방법을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="cdad4-108">Introduces how to write a custom data processing extension for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="cdad4-109">데이터 처리 확장 프로그램 구현 준비</span><span class="sxs-lookup"><span data-stu-id="cdad4-109">Preparing to Implement a Data Processing Extension</span></span>](preparing-to-implement-a-data-processing-extension.md)  
 <span data-ttu-id="cdad4-110">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램을 구현할 때 및 특정 인터페이스를 구현해야 할 때 사용할 수 있는 인터페이스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cdad4-110">Describes the interfaces available when implementing an [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, as well as when you are required to implement a particular interface.</span></span>  
  
 [<span data-ttu-id="cdad4-111">데이터 처리 확장 라이브러리 만들기</span><span class="sxs-lookup"><span data-stu-id="cdad4-111">Creating a Data Processing Extension Library</span></span>](creating-a-data-processing-extension-library.md)  
 <span data-ttu-id="cdad4-112">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램에 대한 네임스페이스 할당에 대해 설명하고 데이터 처리 확장 프로그램을 라이브러리 DLL로 컴파일하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cdad4-112">Describes assigning a namespace for your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension and compiling your data processing extension into a library DLL.</span></span>  
  
 [<span data-ttu-id="cdad4-113">데이터 처리 확장 프로그램에 대한 Connection 클래스 구현</span><span class="sxs-lookup"><span data-stu-id="cdad4-113">Implementing a Connection Class for a Data Processing Extension</span></span>](implementing-a-connection-class-for-a-data-processing-extension.md)  
 <span data-ttu-id="cdad4-114">연결의 특성 및 데이터 처리 확장 프로그램에 대해 고유의 **Connection** 클래스를 구현하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cdad4-114">Describes the attributes of a connection and how to implement your own **Connection** class for your data processing extension.</span></span>  
  
 [<span data-ttu-id="cdad4-115">데이터 처리 확장 프로그램에 대한 Command 클래스 구현</span><span class="sxs-lookup"><span data-stu-id="cdad4-115">Implementing a Command Class for a Data Processing Extension</span></span>](implementing-a-command-class-for-a-data-processing-extension.md)  
 <span data-ttu-id="cdad4-116">명령의 특성 및 데이터 처리 확장 프로그램에 대해 고유의 **Command** 클래스를 구현하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cdad4-116">Describes the attributes of a command, and how to implement your own **Command** class for your data processing extension.</span></span>  
  
 [<span data-ttu-id="cdad4-117">데이터 처리 확장 프로그램에 대한 DataReader 클래스 구현</span><span class="sxs-lookup"><span data-stu-id="cdad4-117">Implementing a DataReader Class for a Data Processing Extension</span></span>](implementing-a-datareader-class-for-a-data-processing-extension.md)  
 <span data-ttu-id="cdad4-118">데이터 판독기의 특성 및 데이터 처리 확장 프로그램에 대해 고유의 **DataReader** 클래스를 구현하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cdad4-118">Describes the attributes of a data reader and how to implement your own **DataReader** class for your data processing extension.</span></span>  
  
 [<span data-ttu-id="cdad4-119">Reporting Services에서 외부 데이터 세트 사용</span><span class="sxs-lookup"><span data-stu-id="cdad4-119">Using an External Dataset with Reporting Services</span></span>](using-an-external-dataset-with-reporting-services.md)  
 <span data-ttu-id="cdad4-120">사용자 지정 **DataSet** 개체를 보고서 서버에서 사용할 수 있도록 표시하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cdad4-120">Describes how to expose your custom **DataSet** objects to the report server for consumption.</span></span>  
  
 [<span data-ttu-id="cdad4-121">데이터 처리 확장 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="cdad4-121">Deploying a Data Processing Extension</span></span>](deploying-a-data-processing-extension.md)  
 <span data-ttu-id="cdad4-122">데이터 처리 확장 프로그램을 배포하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cdad4-122">Describes how to deploy your data processing extension.</span></span>  
  
 [<span data-ttu-id="cdad4-123">데이터 처리 확장 프로그램 코드 디버깅</span><span class="sxs-lookup"><span data-stu-id="cdad4-123">Debugging Data Processing Extension Code</span></span>](debugging-data-processing-extension-code.md)  
 <span data-ttu-id="cdad4-124">데이터 처리 확장 프로그램에서 코드를 디버깅하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cdad4-124">Describes how to debug code in your data processing extensions.</span></span>  
  
 [<span data-ttu-id="cdad4-125">데이터 처리 확장 프로그램 제거</span><span class="sxs-lookup"><span data-stu-id="cdad4-125">Removing a Data Processing Extension</span></span>](removing-a-data-processing-extension.md)  
 <span data-ttu-id="cdad4-126">보고서 서버 또는 보고서 디자이너에서 데이터 처리 확장 프로그램을 제거하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cdad4-126">Describes how to remove a data processing extension from a report server or Report Designer.</span></span>  
  
 <span data-ttu-id="cdad4-127">완전히 구현된 데이터 처리 확장 프로그램 예는 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cdad4-127">For a sample of a fully implemented data processing extension, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdad4-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cdad4-128">See Also</span></span>  
 <span data-ttu-id="cdad4-129">[Reporting Services 확장](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="cdad4-129">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="cdad4-130">Reporting Services 확장 프로그램 라이브러리</span><span class="sxs-lookup"><span data-stu-id="cdad4-130">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
