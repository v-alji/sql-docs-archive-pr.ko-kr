---
title: Azure Blob 원본 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobsrc.f1
- sql11.dts.designer.afpblobsrc.f1
ms.assetid: 80645c5c-88c8-4fb0-8607-de1bb7bffcbb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a14c7022437c8a23f898a0f29c211bd9ae82aa0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660092"
---
# <a name="azure-blob-source"></a><span data-ttu-id="5343c-102">Azure Blob 원본</span><span class="sxs-lookup"><span data-stu-id="5343c-102">Azure Blob Source</span></span>
 <span data-ttu-id="5343c-103">SSIS 패키지는 **Azure Blob 원본** 구성 요소를 통해 Azure Blob에서 데이터를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5343c-103">The **Azure Blob Source** component enables an SSIS package to read data from an Azure blob.</span></span> <span data-ttu-id="5343c-104">지원되는 파일 형식은 CSV 및 AVRO입니다.</span><span class="sxs-lookup"><span data-stu-id="5343c-104">The supported file formats are: CSV and AVRO.</span></span> <span data-ttu-id="5343c-105">Azure Blob 원본용 편집기를 표시하려면 데이터 흐름 디자이너에서 **Azure Blob 원본** 을 끌어서 놓고 두 번 클릭하여 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5343c-105">To see the editor for the Azure Blob Source, drag and drop **Azure Blob Source** on the data flow designer and double-click it to open the editor).</span></span>  
  
1.  <span data-ttu-id="5343c-106">**Azure Storage 연결 관리자** 필드에서는 기존 Azure Storage 연결 관리자를 지정하거나 Azure Storage 계정을 참조하는 스토리지 연결 관리자를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5343c-106">For the **Azure storage connection manager** field, specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account.</span></span>  
  
2.  <span data-ttu-id="5343c-107">**Blob 컨테이너 이름** 필드에서는 원본 파일을 포함하는 Blob 컨테이너의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5343c-107">For the **Blob container name** field, specify the name of the blob container that contains source files.</span></span>  
  
3.  <span data-ttu-id="5343c-108">**Blob 이름** 필드에서는 Blob의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5343c-108">For the **Blob name** field, specify the path for the blob.</span></span>  
  
4.  <span data-ttu-id="5343c-109">**Blob 파일 형식** 필드에서는 사용할 Blob 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5343c-109">For the **Blob file format** field, specify the blob format you want to use.</span></span>  
  
5.  <span data-ttu-id="5343c-110">파일 형식이 CSV이면 **열 구분 기호 문자** 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5343c-110">If the file format is CSV, you must specify the **Column delimiter character** value.</span></span> <span data-ttu-id="5343c-111">또한 파일의 첫 번째 행에 열 이름이 포함 된 경우 **첫 번째 데이터 행에서 열 이름을** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5343c-111">Also select **Column names in the first data row** if the first row in the file contains column names.</span></span>  
  
6.  <span data-ttu-id="5343c-112">연결 정보를 지정한 다음 **열** 페이지로 전환하여 SSI 데이터 흐름에 대해 원본 열을 대상 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="5343c-112">After specifying the connection information, switch to the **Columns** page to map source columns to destination columns for the SSIS data flow.</span></span>  
  
  
