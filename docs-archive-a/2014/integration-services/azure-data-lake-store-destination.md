---
title: Azure Data Lake Store 대상 | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSDEST.F1
- SQL11.DTS.DESIGNER.AFPADLSDEST.F1
ms.assetid: d0e86032-2a6b-48b2-898f-e94328474fde
author: yualan
ms.author: chugu
ms.openlocfilehash: 14248d14b6a944250c33a19c8cf83ab0e0330587
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740228"
---
# <a name="azure-data-lake-store-destination"></a><span data-ttu-id="e6d50-102">Azure Data Lake Store 대상</span><span class="sxs-lookup"><span data-stu-id="e6d50-102">Azure Data Lake Store Destination</span></span>
  <span data-ttu-id="e6d50-103">**Azure Data Lake Store 대상** 구성 요소를 사용하면 SSIS 패키지가 Azure Data Lake Store에 데이터를 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6d50-103">The **Azure Data Lake Store Destination** component enables an SSIS package to write data to an Azure Data Lake Store.</span></span> <span data-ttu-id="e6d50-104">지원되는 파일 형식은 텍스트, Avro 및 ORC입니다.</span><span class="sxs-lookup"><span data-stu-id="e6d50-104">The supported file formats are: Text, Avro and ORC.</span></span> 
  
## <a name="configure-the-azure-data-lake-store-destination"></a><span data-ttu-id="e6d50-105">Azure Data Lake Store 대상 구성</span><span class="sxs-lookup"><span data-stu-id="e6d50-105">Configure the Azure Data Lake Store Destination</span></span> 

1. <span data-ttu-id="e6d50-106">**Azure Data Lake Store 대상** 을 데이터 흐름 디자이너에 끌어서 놓은 다음 두 번 클릭하여 편집기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d50-106">Drag-drop **Azure Data Lake Store Destination** to the data flow designer and double-click it to see the editor.</span></span>  

2.  <span data-ttu-id="e6d50-107">**Azure Data Lake Store 연결 관리자** 필드에서는 기존 Azure Data Lake Store 연결 관리자를 지정하거나 Azure Data Lake Store 서비스를 참조하는 연결 관리자를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e6d50-107">For the **Azure Data Lake Store connection manager** field, specify an existing Azure Data Lake Store Connection Manager or create a new one that refers to an Azure Data Lake Store service.</span></span>  
  
    1.  <span data-ttu-id="e6d50-108">**파일 경로** 필드에서는 데이터를 기록할 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d50-108">For the **File Path** field, specify the file name you want to write data to.</span></span> <span data-ttu-id="e6d50-109">이 파일이 이미 있는 경우 해당 콘텐츠를 덮어쓰게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6d50-109">If this file already exist, its content will be overwritten.</span></span>  
  
    2.  <span data-ttu-id="e6d50-110">**파일 형식** 필드에서는 사용할 파일 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d50-110">For the **File format** field, specify the file format you want to use.</span></span>  
  
        <span data-ttu-id="e6d50-111">파일 형식이 Text이면 **열 구분 기호 문자** 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d50-111">If the file format is Text, you must specify the **Column delimiter character** value.</span></span> <span data-ttu-id="e6d50-112">파일의 첫 행에 열 이름을 포함하려는 경우에는 **첫 번째 데이터 행의 열 이름** 도 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d50-112">Also  select **Column names in the first data row** if the first row in the file contains column names.</span></span>  

        <span data-ttu-id="e6d50-113">파일 형식이 ORC이면 해당 플랫폼의 JRE를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d50-113">If the file format is ORC, you need to install JRE of corresponding platform.</span></span> 
  
3.  <span data-ttu-id="e6d50-114">연결 정보를 지정한 다음 **열** 페이지로 전환하여 SSI 데이터 흐름에 대해 원본 열을 대상 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="e6d50-114">After specifying the connection information, switch to the **Columns** page to map source columns to destination columns for the SSIS data flow.</span></span>  
