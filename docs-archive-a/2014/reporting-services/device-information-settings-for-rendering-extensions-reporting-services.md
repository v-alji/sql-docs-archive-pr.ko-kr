---
title: 렌더링 확장 프로그램에 대한 디바이스 정보 설정(Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 947b0ee1-bb35-4b4e-9527-dc501566e7d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f15e27e01cd43bafda3aede3deca7729f2c89756
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735083"
---
# <a name="device-information-settings-for-rendering-extensions-reporting-services"></a><span data-ttu-id="57fdf-102">렌더링 확장 프로그램에 대한 디바이스 정보 설정(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="57fdf-102">Device Information Settings for Rendering Extensions (Reporting Services)</span></span>
  <span data-ttu-id="57fdf-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에서 디바이스 정보 설정을 사용하여 렌더링 매개 변수를 렌더링 확장 프로그램으로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57fdf-103">In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], device information settings are used to pass rendering parameters to a rendering extension.</span></span> <span data-ttu-id="57fdf-104">각 렌더링 확장 프로그램에서 특정 설정 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57fdf-104">Each rendering extension accepts a specific set of settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57fdf-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="57fdf-105">In This Section</span></span>  
  
|<span data-ttu-id="57fdf-106">항목</span><span class="sxs-lookup"><span data-stu-id="57fdf-106">Topic</span></span>|<span data-ttu-id="57fdf-107">Description</span><span class="sxs-lookup"><span data-stu-id="57fdf-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="57fdf-108">ATOM 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="57fdf-108">ATOM Device Information Settings</span></span>](../../2014/reporting-services/atom-device-information-settings.md)|<span data-ttu-id="57fdf-109">Atom 호환 렌더링 출력과 연관된 디바이스 정보 설정을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="57fdf-109">Describes the device information settings that are associated with Atom compliant rendering output.</span></span>|  
|[<span data-ttu-id="57fdf-110">CSV 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="57fdf-110">CSV Device Information Settings</span></span>](csv-device-information-settings.md)|<span data-ttu-id="57fdf-111">CSV 렌더링 출력과 연관된 디바이스 정보 설정을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="57fdf-111">Describes the device information settings that are associated with CSV rendering output.</span></span>|  
|[<span data-ttu-id="57fdf-112">Excel 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="57fdf-112">Excel Device Information Settings</span></span>](excel-device-information-settings.md)|<span data-ttu-id="57fdf-113">Excel 렌더링 출력과 연관된 디바이스 정보 설정을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="57fdf-113">Describes the device information settings that are associated with Excel rendering output.</span></span>|  
|[<span data-ttu-id="57fdf-114">Word 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="57fdf-114">Word Device Information Settings</span></span>](word-device-information-settings.md)|<span data-ttu-id="57fdf-115">Word 렌더링 출력과 연관된 디바이스 정보 설정을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="57fdf-115">Describes the device information settings that are associated with Word rendering output.</span></span>|  
|[<span data-ttu-id="57fdf-116">HTML 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="57fdf-116">HTML Device Information Settings</span></span>](html-device-information-settings.md)|<span data-ttu-id="57fdf-117">HTML 렌더링 출력과 연관된 디바이스 정보 설정을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="57fdf-117">Describes the device information settings that are associated with HTML rendering output.</span></span>|  
|[<span data-ttu-id="57fdf-118">이미지 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="57fdf-118">Image Device Information Settings</span></span>](image-device-information-settings.md)|<span data-ttu-id="57fdf-119">IMAGE 렌더링 출력과 연관된 디바이스 정보 설정을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="57fdf-119">Describes the device information settings that are associated with IMAGE rendering output.</span></span>|  
|[<span data-ttu-id="57fdf-120">MHTML 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="57fdf-120">MHTML Device Information Settings</span></span>](mhtml-device-information-settings.md)|<span data-ttu-id="57fdf-121">MHTML 렌더링 출력과 연관된 디바이스 정보 설정을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="57fdf-121">Describes the device information settings that are associated with MHTML rendering output.</span></span>|  
|[<span data-ttu-id="57fdf-122">PDF 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="57fdf-122">PDF Device Information Settings</span></span>](pdf-device-information-settings.md)|<span data-ttu-id="57fdf-123">PDF 렌더링 출력과 연관된 디바이스 정보 설정을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="57fdf-123">Describes the device information settings that are associated with PDF rendering output.</span></span>|  
|[<span data-ttu-id="57fdf-124">XML 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="57fdf-124">XML Device Information Settings</span></span>](xml-device-information-settings.md)|<span data-ttu-id="57fdf-125">XML 렌더링 출력과 연관된 디바이스 정보 설정을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="57fdf-125">Describes the device information settings that are associated with XML rendering output.</span></span>|  
|[<span data-ttu-id="57fdf-126">RGDI 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="57fdf-126">RGDI Device Information Settings</span></span>](rgdi-device-information-settings.md)|<span data-ttu-id="57fdf-127">RGDI 렌더링 출력과 연관된 디바이스 정보 설정을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="57fdf-127">Describes the device information settings that are associated with RGDI rendering output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57fdf-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57fdf-128">See Also</span></span>  
 [<span data-ttu-id="57fdf-129">RSReportServer.Config의 렌더링 확장 프로그램 매개 변수 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="57fdf-129">Customize Rendering Extension Parameters in RSReportServer.Config</span></span>](customize-rendering-extension-parameters-in-rsreportserver-config.md)  
  
  
