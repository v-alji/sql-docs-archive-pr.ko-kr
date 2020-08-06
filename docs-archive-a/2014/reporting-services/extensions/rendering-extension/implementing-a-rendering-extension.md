---
title: 렌더링 확장 프로그램 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03deb7c818de8d875f69b585ae6015fc178e707d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651528"
---
# <a name="implementing-a-rendering-extension"></a><span data-ttu-id="32da0-102">렌더링 확장 프로그램 구현</span><span class="sxs-lookup"><span data-stu-id="32da0-102">Implementing a Rendering Extension</span></span>
  <span data-ttu-id="32da0-103">렌더링 확장 프로그램은 보고서 데이터 및 레이아웃 정보를 디바이스별 형식으로 변환하는 보고서 서버의 구성 요소 또는 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="32da0-103">A rendering extension is a component or module of a report server that transforms report data and layout information into a device-specific format.</span></span> <span data-ttu-id="32da0-104">SQL Server Reporting Services에는 HTML, Excel, Word, CSV 또는 텍스트, XML, 이미지 및 PDF의 6가지 렌더링 확장 프로그램이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32da0-104">SQL Server Reporting Services includes six rendering extensions: HTML, Excel, Word, CSV or Text, XML, Image, and PDF.</span></span> <span data-ttu-id="32da0-105">추가 렌더링 확장 프로그램을 만들어 다른 형식으로 보고서를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32da0-105">You can create additional rendering extensions to generate reports in other formats.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32da0-106">사용 가능한 렌더링 확장 프로그램을 확인하려면 RSReportServer.config 파일에서 설치된 확장 프로그램 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32da0-106">To determine which rendering extensions are available, you can view the list of installed extensions in the RSReportServer.config file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="32da0-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="32da0-107">In This Section</span></span>  
 [<span data-ttu-id="32da0-108">렌더링 확장 프로그램 개요</span><span class="sxs-lookup"><span data-stu-id="32da0-108">Rendering Extensions Overview</span></span>](rendering-extensions-overview.md)  
 <span data-ttu-id="32da0-109">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]용 사용자 지정 렌더링 확장 프로그램을 작성하는 방법을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="32da0-109">Introduces how to write a custom rendering extension for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="32da0-110">IRenderingExtension 인터페이스 구현</span><span class="sxs-lookup"><span data-stu-id="32da0-110">Implementing the IRenderingExtension Interface</span></span>](implementing-the-irenderingextension-interface.md)  
 <span data-ttu-id="32da0-111">렌더링 확장 프로그램의 특성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32da0-111">Describes the attributes of a rendering extension.</span></span>  
  
 [<span data-ttu-id="32da0-112">렌더링 확장 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="32da0-112">Deploying a Rendering Extension</span></span>](deploying-a-rendering-extension.md)  
 <span data-ttu-id="32da0-113">보고서 서버에 렌더링 확장 프로그램을 배포하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32da0-113">Describes how to deploy a rendering extension on a report server.</span></span>  
  
 [<span data-ttu-id="32da0-114">렌더링 확장 프로그램 제거</span><span class="sxs-lookup"><span data-stu-id="32da0-114">Removing a Rendering Extension</span></span>](removing-a-rendering-extension.md)  
 <span data-ttu-id="32da0-115">보고서 서버에서 렌더링 확장 프로그램을 제거하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32da0-115">Describes how to remove a rendering extension from a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32da0-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="32da0-116">See Also</span></span>  
 <span data-ttu-id="32da0-117">[Reporting Services 확장 프로그램](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="32da0-117">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="32da0-118">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="32da0-118">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
