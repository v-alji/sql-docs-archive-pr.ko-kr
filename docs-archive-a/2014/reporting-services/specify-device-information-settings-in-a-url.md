---
title: URL에 디바이스 정보 설정 지정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 00cd1fdc3b5fbe129ae4d51b220a11bc48b4744c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734939"
---
# <a name="specify-device-information-settings-in-a-url"></a><span data-ttu-id="8ea9e-102">URL에 디바이스 정보 설정 지정</span><span class="sxs-lookup"><span data-stu-id="8ea9e-102">Specify Device Information Settings in a URL</span></span>
  <span data-ttu-id="8ea9e-103">디바이스 정보 설정은 렌더링 확장 프로그램에 전달되는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8ea9e-103">Device information settings are parameters that are passed to a rendering extension.</span></span> <span data-ttu-id="8ea9e-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 보고서 서버 웹 서비스의 메서드를 사용하여 보고서를 렌더링하는 경우 `DeviceInfo` XML 요소가  입력 매개 변수로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ea9e-104">If you use the methods of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Report Server Web service to render a report, a `DeviceInfo` XML element is passed as an input parameter.</span></span> <span data-ttu-id="8ea9e-105">`DeviceInfo` 요소의 자식 요소는 다양한 렌더링 확장 프로그램의 디바이스 정보 설정마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ea9e-105">Child elements of the `DeviceInfo` element are specific to the device information settings of different rendering extensions.</span></span> <span data-ttu-id="8ea9e-106">*rc:tag=value* 매개 변수 문자열을 사용하여 URL에 디바이스 정보 설정을 포함시킬 수 있습니다. 여기서 *tag* 는 액세스되는 디바이스 정보 설정 요소의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="8ea9e-106">You can include device information settings in a URL by using the *rc:tag=value* parameter string, where *tag* is the name of the device information settings element being accessed.</span></span> <span data-ttu-id="8ea9e-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]의 디바이스 정보 설정에 대한 자세한 내용은 [디바이스 정보 설정을 렌더링 확장 프로그램에 전달](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ea9e-107">For more information about device information settings in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ea9e-108">예제</span><span class="sxs-lookup"><span data-stu-id="8ea9e-108">Example</span></span>  
 <span data-ttu-id="8ea9e-109">다음 예에서는 이미지 렌더링 확장 프로그램의 *OutputFormat* 디바이스 정보 설정을 사용하여 지정된 보고서의 형식을 JPEG으로 설정합니다(읽기 쉽도록 줄 바꿈 추가됨).</span><span class="sxs-lookup"><span data-stu-id="8ea9e-109">The following example sets the format of the specified report to JPEG by using the *OutputFormat* device information setting of the image rendering extension (the line breaks have been added for legibility):</span></span>  
  
```  
http://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ea9e-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ea9e-110">See Also</span></span>  
 <span data-ttu-id="8ea9e-111">[URL 액세스&#40;SSRS&#41;](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8ea9e-111">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="8ea9e-112">URL 액세스 매개 변수 참조</span><span class="sxs-lookup"><span data-stu-id="8ea9e-112">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
